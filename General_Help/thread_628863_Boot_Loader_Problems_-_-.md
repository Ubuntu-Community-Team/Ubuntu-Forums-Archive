---
title: "Boot Loader Problems -_-"
date: 2007-12-01
forum: General Help
---

### Post by sekinto on 2007-12-01
Okay, so I hadn't used Microsoft Windows Vista and Mac OS X Leopard on my HP desktop for awhile, so I decided to format the partitions they were on and create more space for my Ubuntu and Gentoo operating systems. But just a few days ago I joined a gaming group and I was going to help them compose music for their game so I needed Windows XP to run Fruity Loops Studio 7 (I hate Wine, and it wasn't even working in Wine)... anyway, when I installed Windows XP I guess Microsoft's Bootloader loaded before GRUB... so now what do I do? I need GRUB to load Ubuntu and Gentoo.

---

### Post by ExBuM on 2007-12-01
I think this could help you :o
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sekinto on 2007-12-01
Thanks. :)

---

### Post by sekinto on 2007-12-01
Okay, so I got GRUB booting first now. Now how to I boot into WIndows from GRUB, I think I need to add this to menu.lst:

title           Microsoft Windows: XP Profesional SP2
root            (hdX,X)
map             (hdX) (hdX)
map             (hdX) (hdX)
makeactive
chainloader +1

But I don't know what to replace the Xs with.
By the way, my XP partition is on:
First Hard Drive
Third Partition (/dev/sda3)

---

### Post by meierfra on 2007-12-01
Post the output of 

```
sudo fdisk -l
```
(l is a lowercase L)

---

### Post by teryowen on 2007-12-01
we need to know wat partition and hard drive is your ubuntu on.

do as stated above:

sudo fdisk -l

post the output.

---

### Post by sekinto on 2007-12-01
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6527    52428096   83  Linux
/dev/sda2            6528        6788     2096482+  82  Linux swap / Solaris
/dev/sda3   *        8096        9729    13125105    7  HPFS/NTFS

Disk /dev/sdd: 503 MB, 503840768 bytes
5 heads, 4 sectors/track, 49203 cylinders
Units = cylinders of 20 * 512 = 10240 bytes
Disk identifier: 0x25cd25cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              12       49204      491913+   6  FAT16

---

### Post by Craigus on 2007-12-01
Try

> title Microsoft Windows: XP Profesional SP2
root (hd0,2)
makeactive
chainloader +1

---

### Post by meierfra on 2007-12-01
title Microsoft Windows: XP Profesional SP2
root (hd0,2)
makeactive
chainloader +1

should do it.

(lost  by a second:))

---

### Post by teryowen on 2007-12-01
After you've added windows to the file you will need to install GRUB onto the MBR do so by booting of a live CD in terminal type the following:

sudo grub
root (hd0,0)
setup (hd0)
quit

this will install grub just make sure that you've added the few lines for windows to the menu.lst file.

---

