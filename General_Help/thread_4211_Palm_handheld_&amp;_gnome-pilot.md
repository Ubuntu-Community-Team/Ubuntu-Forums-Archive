---
title: "Palm handheld &amp; gnome-pilot"
date: 2004-11-12
forum: General Help
---

### Post by iminj on 2004-11-12
I'm not able to sync my Palm Zire PDA with my new Ubuntu installation. I'm trying to do this using a USB connection and gnome-pilot - with no success. Hotsync starts up on the Palm device, and stalls.

Is gnome-pilot "ready-to-go" in the ubuntu installation; or are there other conduits I need to install to sync with Evolution's address book and calendar ? I've been doing this in the Windows world for years, and I'm finding the gnome methodology a little unfamiliar.

Anyone able to walk me thru the set-up ? thanks

Iminj

---

### Post by zenetics on 2004-11-12
Hello !!!

I have a similar problem ! :sad: 

I've got an Infra red connection on my motherboard, and I was really surprise to see it detected on boot an the modules loaded (via-ircc, ir_attach....)
But when I tryed to syncronised the palm with gnome-pilot nothing happened.

If somebody knows how to link my (old) palm IIIx He would be very kind.

Tanks for replying


PS : Sorry for the mistakes but my english is far from perfect

Zenetics

---

### Post by TravisNewman on 2004-11-12
This is a great place to start:
[http://howtos.linuxbroker.com/PalmOS-HOWTO.html](http://howtos.linuxbroker.com/PalmOS-HOWTO.html)

---

### Post by Marauder1 on 2004-11-12
I was able to do it with my handspring easy, the only thing
i had to find out is wich usb port to write down in the config.

ex : try /dev/ttyUSB0 and go up until you can sync.

Mine connected to /dev/ttyUSB1. ( i have a USB scanner also).

If you want everyone to share this then you can make symlink
by doing :  ln -s /dev/ttyUSB1 /dev/pilot (in my case) and change
the config port to /dev/pilot.

Hope it will work for you !!!

---

### Post by iminj on 2004-11-12
B-I-N-G-O !!!

Marauder1: Thanks for the tip on configuring USB ports. I didn't know how to do that 'til you posted the advice. In my case it was: /dev/ttyUSB1   ... and I was then able to finish configuring my Palm PDA and the various conduits. Hotsync worked perfectly after that.

panickedthumb: The HOWTO link you posted is an excellent overview of Palm - Linux and is bookmarked. Thank you.

UBUNTU Community is GREAT !!

iminj

---

### Post by TravisNewman on 2004-11-12
Yeah I think it's consistently ttyUSB1, no matter what devices I have connected it uses ttyUSB1. That may be malarkey though, so take it with a grain of salt.

If you wanna sync to Evolution, in the conduit list, they're the ones that begin with a capital E.

And to reply to iminj, yes the community is great. It's the reason I'm using Ubuntu exclusively. You can make the best software in the world, but if it doesn't have a good community behind it, its missing a LOT.

---

### Post by artAlexion on 2004-11-21
[QUOTE=iminj]B-I-N-G-O !!!

Marauder1: Thanks for the tip on configuring USB ports. I didn't know how to do that 'til you posted the advice. In my case it was: /dev/ttyUSB1   ... and I was then able to finish configuring my Palm PDA and the various conduits. Hotsync worked perfectly after that.

panickedthumb: The HOWTO link you posted is an excellent overview of Palm - Linux and is bookmarked. Thank you.

UBUNTU Community is GREAT !!

iminj[/QUOTE]
 I have no /dev/ttyUSB#.  although dmesg reports:
> usb 1-1: new full speed USB device using address 2
drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
usbcore: registered new driver usbserial_generic
usbcore: registered new driver usbserial
drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
usb 1-1: palm_os_4_probe - error -32 getting connection info
visor 1-1:1.0: Handspring Visor / Palm OS converter detected
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
usbcore: registered new driver visor
drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver v2.1

---

### Post by randy on 2004-11-21
The usb devices will only be there during the sync process.  As soon as the sync attempt has ended the devices won't be there.

---

### Post by artAlexion on 2004-11-24
OK, then what block device do I select when configuring gnome-pilot? :???:

---

