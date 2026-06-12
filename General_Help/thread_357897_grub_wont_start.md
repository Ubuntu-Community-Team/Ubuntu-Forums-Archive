---
title: "grub wont start"
date: 2007-02-10
forum: General Help
---

### Post by hempa on 2007-02-10
This is how it goes i have two hard drives i have had windows xp but recently installed ubuntu from a live cd and i choosed the erase whole disk option to clean the hard drive and only have ubuntu on it. I have done this on both my hard drives this is how it looks now

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18695   150167556   83  Linux
/dev/sda2           18696       19452     6080602+   5  Extended
/dev/sda5           18696       19452     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18695   150167556   83  Linux
/dev/sdb2           18696       19452     6080602+   5  Extended
/dev/sdb5           18696       19452     6080571   82  Linux swap / Solaris
ubuntu@ubuntu:~$


grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0x83

i hope this can be of some help.

my problem is that when i restart my computer without the live cd grub wont start it just says grub loading and then it freezes. and on my boot menu in bios none of my two hard drives is shown.
how can i get grub to work or boot any of my two hard drives to use ubuntu.
 please help me

---

### Post by geek_Man on 2007-02-11
Which drive has your /boot folder? Sda or sdb? And can you post your menu.lst file?

---

