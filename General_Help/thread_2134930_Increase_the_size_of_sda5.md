---
title: "Increase the size of sda5"
date: 2013-04-12
forum: General Help
---

### Post by LumbeeNDN on 2013-04-12
Here is the df output...
  
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        42G   40G  754M  99% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  912K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  324K  3.9G   1% /run/shm
/dev/sda1       248G  188M  235G   1% /media/vol2
```



   I would like to 'extend'..'add to' (not sure what term I should use  here) sda5 with space from sda1. Currently my OS lives on sda5, so I  would like to do this without losing any data.

---

### Post by papibe on 2013-04-12
Hi LumbeeNDN.

These would be the general steps:
[LIST]
[*]Backup your personal data. Although the following steps do not destruct data, there's always the possibility of an unforeseen error.
[*]Use your installation media as a Live CD/USB to do this (you can't modify a partition which is being used).
[*]Use 'gparted to do the job (available on the installation media).
[*]Now I'm going to assume your partitions are in this order: sda5, sda1, swap area. This is what I would do inside gparted:
[LIST]
[*][*]Shrink sda1. This would crate space at the end of sda1.
[*][*]Move sda1 through the end of the disk so the free space would be now between sda1 and sda5.
[*][*]Resize sda5 so it would take advantage of the free whole space.
[/LIST]
[*]If your partitions are in a different order different steps would be necessary, but I believe you are getting the main idea.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by LumbeeNDN on 2013-04-12
Oh, so that is the other thing I forgot to mention. When I try to boot to a usb I get the error 'Invalid Partiontion'. I previously had Windows 7 installed on this laptop, and I am wondering if that is the issues. When booting to USB would the partitions/grub loader have any bearing on that?

---

### Post by papibe on 2013-04-12
That's very unlikely.

My guess is the USB was not properly created, or it got modified somehow.

If you have an Ubuntu ISO, try using 'Start Up Disk Creator' to re create the USB.

Regards.

---

### Post by LumbeeNDN on 2013-04-15
Thanks guys. Yes, the issue was I had was a bad boot usb. I was able to use Gparted to expand the partition.

---

