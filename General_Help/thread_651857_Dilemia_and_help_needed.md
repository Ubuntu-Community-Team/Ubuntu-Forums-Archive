---
title: "Dilemia and help needed"
date: 2007-12-28
forum: General Help
---

### Post by Dante Xaiver on 2007-12-28
i have installed and uninstalled ubuntu several times in the last month not totally ready to emancipate my self from the bloat ware that is windows its like cutting your self off from those you love its just not easy to do when windows is all you have ever known dont get me wrong i love ubuntu but just feels weir with out windows thats all 

when im done downloading the 50 gb of data i have in azerous right now i will format and go completely with ubuntu but how do i get ubuntnu to rea and write to my ntfs formated external drives i mean i pulled my hair out trying to figure out how to get linux to support them but to no avail and losing my data in the process

---

### Post by delphiguy on 2007-12-28
I think Ubuntu 7.10 comes with ntfs-3g, so you should be able to read/write
to your ntfs partitioned harddisk.

In my system ntfs read/write just works so I am assuming that it is already
on by default.

---

### Post by Dante Xaiver on 2007-12-28
i tryed  7.10  and  wasnt able to mount the usb hard drive  .  i have  a sata 500 gb hard drive that i put  into an usb enclosure as im using a laptop

---

### Post by delphiguy on 2007-12-28
I have a 400GB usb enclosure and it automounts the drive whenever I plug it in.

What does fdisk show?
sudo fdisk -l

---

### Post by Dante Xaiver on 2007-12-28
fdisk shows 

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         490     3935893+  82  Linux swap / Solaris
/dev/sda2   *         491       11978    92277360   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2979ce91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS
dante@dante-laptop:~$

---

### Post by Sef on 2007-12-28
> I think Ubuntu 7.10 comes with ntfs-3g, so you should be able to read/write
to your ntfs partitioned harddisk.


Check Applications > Add/Remove > Search > type in ntfs > enter > if ntfs-3g is checked it is installed; if not, then check it and click apply to install it.

---

### Post by Dante Xaiver on 2007-12-28
it is installed       but when i try to mount it it says can not mount volume

---

### Post by Dante Xaiver on 2007-12-28
was trying a work around  but i cant save  the fstab file   says i dotn have permision wtf how do i fix this

---

### Post by Dante Xaiver on 2007-12-28
ok thanx for the help guys i got it to work  with some fiddling around god damn im such a noob  :lolflag::guitar:  now time to install wine and say good by to  shackles called windows that have kept me down  


Long live LINUX WOOT

---

