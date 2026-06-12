---
title: "Live USB Boot Device changes based on system"
date: 2014-03-07
forum: General Help
---

### Post by montydepaola on 2014-03-07
I have built a custom Live USB system but cannot find a way to set the boot device to a constant value and make it read/write.  I have several scripts and log files that need to be ran and written to and need a constant way of mounting the boot device such as making it /mnt/usbboot or simply /usbroot and then making it rw.

I have tried to add the following to fstab but that is ignored as the device is already mounted in mtab
/dev/disk/by-label/NN  /usbroot     vfat   auto,rw,exec,noatime,nodiratime,umask=0,shortname=mixed  0  0

With the Live USB the root of the USB key is mounted as CDROM or CDROM? from within mtab if you have one or more CDROM's already in the system.  I have extracted the iso and looked at the mtab file and there is no entry in it for the boot device so it must be being set to the first available CDROM? from a script within the initrd.lz

I extracted the initrd.lz and looked within the scripts but cannot find any way of setting this up.  The only place I did see something was in the 05mountpoints script which has,
mkdir -p /root/cdrom
mount -n -o move /cdrom /root/cdrom

I change these to 
mkdir -p /root/usbroot
mount -n -o move /usbroot /root/usbroot

This created an empty folder at /usbroot but the root of the usb drive is still mounted at /cdrom and is read only and the entry in the mtab after boot was /dev/sr0 /cdrom4

Thanks for any help

---

### Post by montydepaola on 2014-03-08
Figured this out, nothing to do with mtab or the boot, it was a very bad written script that was pulling and labeling usb dongles

---

