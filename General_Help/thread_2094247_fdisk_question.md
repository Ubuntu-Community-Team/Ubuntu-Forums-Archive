---
title: "fdisk question"
date: 2012-12-13
forum: General Help
---

### Post by CaptainMark on 2012-12-13
When formatting a usb via the terminal I know theres many options of tools to use but can someone explain the difference between these methods,
1. Using fdisk to create the partition size and using mkfs.vfat to create the filesystem
2. Using fdisk to create the partition and filesystem with the W95 FAT32 option,
Both methods create a usb which will show up in gparted as FAT32 filesystem but a quick "fdisk -l" will show method 1 as a linux filesystem and method 2 shows as FAT32 filesystem

I thought option 1 still created a FAT32 filesystem, obviously I am wrong but could anyone shed any light on this, whats the difference between VFAT and FAT32 and can I take either option and plug my usb into any other computer including Windows computers and it work okay.

Many thanks
Mark

---

### Post by vanadium on 2012-12-13
The mkfs command does only format, but does not fill out a file system identifier, a code that informs about what file system was used. You would need to do that yourself with fdisk.

When you also format through fdisk, fdisk takes also care to update the file system identifier appropriately.

In both cases, you created a dos file system. As far as I know, there are, for practical purposes, no issues if you do not update the file system identifier.

---

### Post by CaptainMark on 2012-12-13
Okay thanks, so in effect I'm not wrong about the filesystems being the same but mkfs does not identify the filesystem in the same way,

Will Windows detect the partition without the identifier or will it reject it and my usb wont work?

---

