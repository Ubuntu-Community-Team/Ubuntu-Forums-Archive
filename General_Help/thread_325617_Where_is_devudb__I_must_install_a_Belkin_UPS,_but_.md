---
title: "Where is /dev/udb ??? I must install a Belkin UPS, but a can't find my USB perifical."
date: 2006-12-26
forum: General Help
---

### Post by antoinel12 on 2006-12-26
I received an UPS for Christmas. I tried to install it on my Ubuntu's Server computer (Ubuntu Server 6.10). But Bulldog Apps can't find my UPS. I searched the path /dev/USB ant it doesn't exist...

Do I need to configure something to make it work???

Thanks a lot,

Antoine L.

---

### Post by logos34 on 2006-12-26
Belkin offers linux support for serial ups, not usb.  

Try the nut-ups package (universe), has some USB UPS Drivers.

enter this

$ lsusb

does it show up?

---

### Post by antoinel12 on 2006-12-26
It show me that:

Bus 001 Device 003: ID 047d:1001 Kensington
Bus 001 Device 002: ID 050d:0751 Belkin Components
Bus 001 Device 001: ID 0000:0000

I can't get mounted my USB in /dev/usb

In the installation procedure, they ask me to specify the port where it's plugged:

If it's pluged on serial port enter : /dev/tty...
Or if i'ts on USB enter /dev/usb

---

### Post by antoinel12 on 2006-12-26
This is what i see: [IMG]http://www.antoinel12.is-a-geek.net/ups.png[/IMG]

---

### Post by antoinel12 on 2006-12-27
Do I need to mount /proc/bus/usb/001/002 or what?

---

