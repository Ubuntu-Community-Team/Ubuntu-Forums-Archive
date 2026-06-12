---
title: "Problem installing a USB printer on a LTSP client"
date: 2008-07-09
forum: General Help
---

### Post by Avinash.Rao on 2008-07-09
Hello,

I am using Ubuntu Studio as LTSP server and i have confiured a network printer which works fine for all the users.
But, there's new HP officejet 4355 All-in one printer which has only a USB port. I have installed the recommended hplip-2.8.6.run binaries, but i am not able to setup the local printer. Coz, when i plug in the printer to the local LTSP client USB port, the OS doesn't detect any device. I guess the USB ports can detect only drives for data storage.


Just to clarify, the local devices option is enabled on the LTSP server. If i plug in a USB drive, the client can detect it without any problems.


How do i make this work??
Avinash

---

### Post by ing_nagel on 2009-07-11
Hola disculpa que no te responda en tu idioma:

Yo también tengo el mismo problema. 
Implemente lo que dice el manual:
IP estática en el cliente LTSP en dhcpd.conf

Activé los dispositivos locales en lts.conf

LOCALDEV=TRUE
PRINTER_0_DEVICE=/dev/usblp0
PRINTER_0_TYPE=U
PRINTER_0_PORT=9100

y ademas agregue
MODULE=usblp

NO FUNCIONO!!!!!

Donde tengo duda es /dev/usblp0, ya que al conectar el dispositivo usb lo debería reconocer, pero no es así ya lo revise. Tambien hay un comentario [https://help.ubuntu.com/community/UbuntuLTSP/TroubleShooting](https://help.ubuntu.com/community/UbuntuLTSP/TroubleShooting) hay que modificar un parametro de start_printer 0 en el inittab en /opt/ltsp/i386/etc del cliente, sin embargo ese archivo en ubuntu no existe.

TAMBIEN estoy atorado aqui!!!!

ALGUIEN nos puede dar un poquito de ayuda por favor!!!
GRACIAS

---

### Post by Avinash.Rao on 2009-07-20
Hi, 

Here's my lts.conf file. 

[default]
    X_COLOR_DEPTH=16
    LOCALDEV=True
    SOUND=True
    NBD_SWAP=True
    SYSLOG_HOST=server
    
# A Thin Client Printer
[00:02:B3:93:EC:98]
    PRINTER_0_DEVICE=/dev/usblp0
    PRINTER_0_TYPE=U
    SCREEN_07=shell
    PRINTER_0_PORT=9100

I have assigned a static IP for this MAC address in DHCP. I have also loaded usblp module. How do i install the printer on the LTSP client. I tried adding, but it didn't detect nor i could print after installing. 

I went through the documentation and my server doesn't have /opt/ltsp/i386/etc/inittab file. 

Should I start the USBLP module in chroot or on server? 

Please help
Avinash


> **ing_nagel said:**
> Hola disculpa que no te responda en tu idioma:

Yo también tengo el mismo problema. 
Implemente lo que dice el manual:
IP estática en el cliente LTSP en dhcpd.conf

Activé los dispositivos locales en lts.conf

LOCALDEV=TRUE
PRINTER_0_DEVICE=/dev/usblp0
PRINTER_0_TYPE=U
PRINTER_0_PORT=9100

y ademas agregue
MODULE=usblp

NO FUNCIONO!!!!!

Donde tengo duda es /dev/usblp0, ya que al conectar el dispositivo usb lo debería reconocer, pero no es así ya lo revise. Tambien hay un comentario [https://help.ubuntu.com/community/UbuntuLTSP/TroubleShooting](https://help.ubuntu.com/community/UbuntuLTSP/TroubleShooting) hay que modificar un parametro de start_printer 0 en el inittab en /opt/ltsp/i386/etc del cliente, sin embargo ese archivo en ubuntu no existe.

TAMBIEN estoy atorado aqui!!!!

ALGUIEN nos puede dar un poquito de ayuda por favor!!!
GRACIAS

---

### Post by zunaidius on 2012-07-26
I have a same problem, which i used EDUBUNTU 12.04 and the
make static IP client (/etc/ltsp/dhcpd.conf) and setting    	 	 	 	 	/var/lib/tftpboot/ltsp/i386*/*[I][I]lts.conf

thank's

Andi
[/I][/I]

---

