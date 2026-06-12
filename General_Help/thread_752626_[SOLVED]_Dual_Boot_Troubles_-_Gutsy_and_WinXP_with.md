---
title: "[SOLVED] Dual Boot Troubles - Gutsy and WinXP with GRUB"
date: 2008-04-11
forum: General Help
---

### Post by kreuelt on 2008-04-11
I need some help setting up my menu.lst. Sorry in advance, I know there are a million threads like this already, but none of them seemed to help.
Here's my information:
//My menu.lst looks like this (with all the preliminary comments removed)

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1

title		Ubuntu Linux
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fea2d57-9e67-44af-acdd-e4a1af75a889 ro vga=789
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6fea2d57-9e67-44af-acdd-e4a1af75a889 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

//sudo fdisk -l returns this

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006cd43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00084dcc

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+   7  HPFS/NTFS
/dev/hda2           14217       14593     3028252+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3916    31455238+   c  W95 FAT32 (LBA)
/dev/hdb2            3917        7294    27133785    c  W95 FAT32 (LBA)

//My device.map looks like this

(hd0)	/dev/sda
(hd1)	/dev/hda

In case you were wondering, I'll explain my hard drive setup
/dev/sda is a 250GB SATA drive with Ubuntu Gutsy on it.
/dev/hda is a 120GB IDE drive with Windows XP on it.
/dev/hdb is a 60GB IDE drive partitioned to two 30(ish)GB partitions, and formatted to FAT32, for trading files between Windows and Linux.
Windows is on /dev/hda1

Does anyone have any suggestions?

---

### Post by Gauvenator on 2008-04-11
Windows doesn't like being on the second hardrive.
So in your menu.lst, change your windows entry to this:

title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

Mapping tricks windows into thinking it's on the first harddisk.

---

### Post by kreuelt on 2008-04-11
Thank you lots! I'm posting this from Windows :-D
Marking this problem as Solved.

---

### Post by Gauvenator on 2008-04-11
You're welcome.  Glad I could help.

---

### Post by Nerocon on 2008-04-14
Does mapping work with partitions? not to hijack your thread but I have a similar problem.

---

