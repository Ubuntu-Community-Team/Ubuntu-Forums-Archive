---
title: "boot device settings"
date: 2013-02-21
forum: General Help
---

### Post by NoobKing on 2013-02-21
Sometimes when i boot up i get this message.
[Picture]("http://img694.imageshack.us/img694/6858/0220132246.jpg")

When i uninstall the nvidia driver it wont come up. I have reinstalled and looked all over for how to try to fix it. Everytime i install the driver it comes back. This all started after an update a few days ago.

Card: GeForce GTX 480
Ubuntu 12.04 64bit

I use the additional driver program to install the drivers. I use them for steam. If anyone has any suggestions i would appreciate it.

---

### Post by dino99 on 2013-02-21
from synaptic:
- purge ALL the installed graphic drivers
- add that ppa to get the nvidia 313.18 driver
- update 
- when the 313 driver is installed, then deactivate that ppa & update again
- reinstall "nouveau"

in case you have an xorg.conf, remove it & let the kernel dealing with X alone

sudo rm /etc/X11/xorg.conf

then reboot

):P

---

### Post by NoobKing on 2013-02-21
thank you so much. That fixed it all.

---

