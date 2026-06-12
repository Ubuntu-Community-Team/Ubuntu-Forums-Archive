---
title: "/media - Why"
date: 2007-12-17
forum: General Help
---

### Post by CanonKen on 2007-12-17
Anyone explain why I have these files in /media, some are the same drives

1. sdb1 is my 2nd hard drive yet there is a folder called disk in there and its the same drive as sdb1, same files showing thats on the drive.
2. Why do I have floppy and floppy0 but only have 1 floppy drive :confused:
3. Why do I have cdrom, cdrom1 and cdrom0 but I only have 2 cdrom drives :confused:

Heres output from  sudo fdisk -l 

```
ken@ubuntu:~$ sudo fdisk -l 
[sudo] password for ken:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b9f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375        8572    17655435   83  Linux
/dev/sda3            8573        8703     1052257+  82  Linux swap / Solaris
/dev/sda4            8704       48641   320801985   83  Linux

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda0bda0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661   83  Linux
ken@ubuntu:~$ 

```

---

### Post by LaRoza on 2007-12-17
The devices are mounted in /media. 

In Linux, everything is a file, even devices.

The mountpoint can be changed if you wanted.

The floppy0 would be the first floppy drive.

In computers, many things are indexed from 0.

---

### Post by CanonKen on 2007-12-17
I understand the 1st three, but when we get to the floppy bit if floppy0 is the 1st floppy drive whats floppy then - the 2nd?? I aint got a 2nd one.
Same for cdrom, cdrom0 is the 1st, cdrom1 2nd? whats cdrom?? thats the bit I can't weigh up

---

### Post by LaRoza on 2007-12-17
cdrom links to the first drive. It looks like the default drive.

---

### Post by diatribe on 2007-12-17
they may also be symlinks, thats why there would be 2

---

### Post by jken146 on 2007-12-17
Yes, cdrom and floppy are just symbolic links to the first drives.  This allows you to set a default drive if you have more than one, and not worry about the numbering.

---

### Post by CanonKen on 2007-12-17
Thanks for the info guys

---

### Post by tgalati4 on 2007-12-17
If you have a disk in the CDROM drive then it will mount with whatever label is contained on the disk.  /media/cdrom and /media/cdrom0 are just placeholders for the kernel to mount a device without a label.

If you don't like the names you can rename them to whatever you want, but you may break the automounting feature of cdrom's and floppies.

---

