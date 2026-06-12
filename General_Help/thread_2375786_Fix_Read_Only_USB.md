---
title: "Fix Read Only USB"
date: 2017-10-27
forum: General Help
---

### Post by Hewjr100 on 2017-10-27
Tried the following:

fsck /dev/sdb
wipefs --all /dev/sdb
mount -o remount,rw /dev/sdb

 This is a new USB flash drive and nothing seems to work.  Any other options I missed.

Henry

---

### Post by kazakore on 2017-10-27
You need a space after he comma in the mount command (but that's probably just a typo on the forum.)

For some reason certain USB keys of mine, despite being FAT formatted, mount as having root as the owner. 

sudo chown user /media/<usbname>

Really shouldn't have to be doing that though!

---

### Post by oldos2er on 2017-10-27
*chown* only works on Linux-native file systems.

---

### Post by kazakore on 2017-10-27
> **oldos2er said:**
> *chown* only works on Linux-native file systems.

No it doesn't. It is only persistent on linux filesystems but for that session it will work on any filesystem.

---

### Post by ajgreeny on 2017-10-27
> **Hewjr100 said:**
> Tried the following:

fsck /dev/sdb
wipefs --all /dev/sdb
mount -o remount,rw /dev/sdb

 This is a new USB flash drive and nothing seems to work.  Any other options I missed.

Henry
Does the USB have a partition table on it?

If not you need to create a PT and then you need to also create a partition on that USB drive as well; trying to work on the whole device, ie, /dev/sdb will cause you difficulties; I'm not even sure it can be done.

Lots of info at [https://askubuntu.com/questions/22381/how-to-format-a-usb-flash-drive](https://askubuntu.com/questions/22381/how-to-format-a-usb-flash-drive) on various ways to do this using GUI or terminal commands.

---

### Post by efflandt on 2017-10-27
What do you see in **dmesg** command in a terminal after you plug in the USB device? Normally partition(s) on a USB device would mount automatically, but /dev/sdb is a device, not a partition. So not sure what you are trying to achieve with wipefs a non-partition and trying to mount a non-partition. The first partition on /dev/sdb would be /dev/sdb1.

---

### Post by kazakore on 2017-10-27
> **ajgreeny said:**
> Does the USB have a partition table on it?


Good call. I'd missed the New bit. I would open GParted and have a look what you see there. Much easier to see and change things if you're unsure of what you're doing.

---

