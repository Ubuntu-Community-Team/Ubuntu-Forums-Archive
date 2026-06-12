---
title: "Can't Change Label on USB Hard drive"
date: 2006-11-30
forum: General Help
---

### Post by atmnerd on 2006-11-30
I'm not sure why this happened, but my USB hard drive has started to mount using the mount point "/media/p Data 5.0". When it is auto deteted by my Dapper laptop. It is formated FAT32 so that I can use it both with Linux at home and Windows at work. It used to always mount as usb or usb-1 (I think). I noticed that my other Windows hard drive partitions (not usb) mount using their Label name. That's the one that shows when you do "ls /dev/disk/by-label -lah"

Here's what I get with /dev/disk/by-label -lah

total 0
drwxr-xr-x 2 root root 100 2006-11-30 06:08 .
drwxr-xr-x 6 root root 120 2006-11-29 18:44 ..
lrwxrwxrwx 1 root root  10 2006-11-29 23:44 DellUtility -> ../../sda1
lrwxrwxrwx 1 root root  10 2006-11-30 06:08 p_Data__5.0 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2006-11-29 23:44 WINXP -> ../../sda2

I used mtools command mlabel to change the label on the the usb drive to USBHD. It seemed to work. The output of "mlabel -s u:" is "Volume label is USBHD", but /dev/disk/by-label -lah still shows "p_Data__5.0" for /sdb1.

What am I doing wrong?

---

### Post by CatKiller on 2006-11-30
Maybe you need to reboot, or remount, or do something else to refresh that list?

---

### Post by atmnerd on 2006-11-30
Tried rebooting. Didn't work. :(

---

