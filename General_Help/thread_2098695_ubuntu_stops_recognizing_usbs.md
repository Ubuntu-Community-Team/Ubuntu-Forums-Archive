---
title: "ubuntu stops recognizing usbs"
date: 2012-12-27
forum: General Help
---

### Post by mythic97 on 2012-12-27
Ubuntu keeps refusing my usbs I can't use my USB dongle or external hard disk please help usbs not shown at all in file browser

---

### Post by rnerwein on 2012-12-27
> **mythic97 said:**
> Ubuntu keeps refusing my usbs I can't use my USB dongle or external hard disk please help usbs not shown at all in file browser
hi
i don't now what version you are running - mine is 12.04 LTS.
hope on your system is the same /sys structure as on mine.
try: 
cat /sys/bus/usb/devices/usb?/authorized_default (or cd /sys/....
all this values should be 1
next
cat  /sys/bus/usb/devices/1-2/authorized
should be 1 
i ain't now your system - therefor cd //sys/bus/usb/devices/
there you will find (i hope) usb1, usb2 .... - in each of these directories you will find the authorize... file. all of them should be one. if they are set to 0 change it with (must be root) e.g.
echo 1 >  /sys/bus/usb/devices/1-2/authorized
it's a change but normaly all of these devices are enabled.
cheers

---

