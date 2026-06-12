---
title: "automount any USB key to fixed point"
date: 2013-11-16
forum: General Help
---

### Post by dudumomo on 2013-11-16
Hi there,

I'd like to automount any USB key to /media/usb
Currently, the system automount the USB key by its label. For example /media/0987-2345
Which is quite annoying in fact for me.

I've tried to modify my fstab to say that /dev/sda will be mounted to /media/usb with defaults options.
However, if I unplug the key and plug in again, the key will be under /dev/sdb and mounted back to /media/0987-2345

Any way to modify this behaviour?

Thank you !

---

### Post by Morbius1 on 2013-11-16
Conceptually, you don't want to mount any usb key to the same mount point. What happens if you are using 2 keys at the same time?
> Currently, the system automount the USB key by its label. For example /media/0987-2345
The system will in fact automatically mount to /media/LABEL ( in the version of Ubuntu you are using ). If a label does not exit it mounts to /media/UUID and "0987-2345" is not a label it's the UUID of a fat32 formatted partition. 

If you want it to mount to /media/usb add a label to the partition. You can use gparted to do that.

---

