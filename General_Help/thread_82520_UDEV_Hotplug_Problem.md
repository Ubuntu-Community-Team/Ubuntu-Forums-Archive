---
title: "UDEV Hotplug Problem"
date: 2005-10-26
forum: General Help
---

### Post by JohnBoyDoe on 2005-10-26
Hi,

i´m trying to get my printer (HP LJ100) to work under Breezy.

I figured out that the problem in ubuntu breezy is the newly changed udev hotplugging stuff.
I will below write what i did and then ask my question:

i created new udev rule

 /etc/udev/rules.d/011_own.rules  

which contents

# HP Laserjet 1000

BUS="usb", SYSFS{idVendor}="03f0", SYSFS{product}="hp LaserJet 1000",NAME="usb/%k", SYMLINK="hplj1000"

This udev rule work because i now have the following devices

/dev/usb/lp0 
/dev/hplj100

i have a working hotplug script in

/etc/hotplug/usb/hplj1000

but i have to start it manually in the terminal before the firmware is uploaded and i can print.

So why is the hotplug script not executed?

Any hints?

Bye
JBD

---

### Post by JohnBoyDoe on 2005-10-30
The solution is to use the RUN+ in the udev rules

BUS="usb", SYSFS{idVendor}="03f0", SYSFS{product}="hp LaserJet 1000",PROGRAMM="/etc/hotplug/usb/hplj1000",NAME="usb/%k", SYMLINK="hplj1000", RUN+="/etc/hotplug/usb/hplj1000" 

happy printing
JBD

---

### Post by essexman on 2005-11-03
JohnBoyDoe

This is a good HOWTO post. Would you consider writing it up and putting it on the [5.10 HOWTO forum]("http://ubuntuforums.org/forumdisplay.php?f=104")?

---

