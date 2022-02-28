Repositorio y HowTo para el proyecto de RocolaPlex.

En la primera etapa queremos que la RocolaPlex sea una computadora que permita extraer (Rippear) 
sin perdida, el audio de nuestros CDs y convertirlos en archivos digitales. Además queremos agregar
a estos archivos de audio, el mayor número posible de metadatos como nombres de archivos, portadas,
páginas internas del librito y letras de canciones.

Para lograr la primera etapa se sugirió la compra de la siguiente lista de componentes:

1- Kit computadora Single Board RaspBerry Pi 4. Se propuso este kit de LABISTS:
https://labists.com/products/raspberry-pi-4-8gb-ram-starter-kit-with-64gb

2- Lector CD-DVD con carga por slot. Se propuso este lector de Blue Ray Multizona:
https://www.amazon.com/gp/product/B0859ZLVBK/ref=ppx_yo_dt_b_asin_title_o00_s01?ie=UTF8&psc=1

3- Disco duro externo USB3 choncho para guardar todo:
https://www.amazon.com/-/es/gp/product/B08DDC36S1/ref=ox_sc_act_title_2?smid=ATVPDKIKX0DER&psc=1

4- Se propone un HUB USB para no tener problemas de potencia con el USB de la RaspBerry:
https://www.amazon.com/dp/B07Q13G9MT/ref=cm_sw_r_wa_awdb_imm_RS4P1THSZWM97CZKAZ45

Se requiere instalar el sistema operativo Raspberry OS Lite de 64bits usando RaspBerry Pi Imager.
https://www.raspberrypi.com/software/ La imagen está en el menú Raspberry Pi OS (Other) del Imager.
Se recomienda preconfigurar el OS desde el botón de engrane del Imager.
Insertar la memoria MicroSD de 64GB del kit en el adaptador blanco de MicroSD a USB e insertarlo en la PC/Mac/Linux. Expulsar el adaptador USB, insertar la memoria MicroSD en la Rapspberry.

Se deberá conectar la Raspberry a la red domestica con cable ethernet, o WiFi si se preconfguró el sistem en del Imager, así como a un monitor HDMI y enceder. Al final del arranque aparece en el monitor un mensage indicando la IP de la Raspberry.

Mediante la IP establecer una conexión SSH con usuario "pi" y contraseña "raspberry" (o la preconfigurada) ya sea desde una terminal (Mac o Linux) o por medio de Putty desde Windows. Posteriormente ejecutar los comandos
como se indica tomando en cuenta que a partir del # son comentarios para entender el comando:

ssh pi@192.168.0.101

passwd # Permite cambiar la contraseña del usuario "pi", se deberá introducir la contraseña anterior

sudo apt update; sudo apt full-upgrade -y # Permite actualizar el sistema a la última versión

sudo reboot # Reiniciar

ssh pi@192.168.0.101 # Volver a conectarse usando el usuario "pi" y la nueva contraseña

Instalar Plex Media Server:
sudo su -
wget -O - https://downloads.plex.tv/plex-keys/PlexSign.key | gpg --dearmor > /usr/share/keyrings/plex.gpg
echo deb [signed-by=/usr/share/keyrings/plex.gpg] https://downloads.plex.tv/repo/deb public main > /etc/apt/sources.list.d/plexmediaserver.list
apt update
apt install plexmediaserver

Verificar que Plex Server funciona:
systemctl status plexmediaserver

Instalar Docker:

https://github.com/rix1337/docker-ripper

