---
title: "Problem with dual boot windows 7 and Ubuntu"
date: 2014-07-24
forum: General Help
---

### Post by luismiguelmalmeida on 2014-07-24
Let me start from the beginning.

Like the title says my idea is having a dual boot with ubuntu and windows 7, so I firstly installed windows 7.

I create a flash drive using Universal USB installer with ubuntu, restart the computer, boot from the usb and ubuntu doesn't recognize that I have windows 7 installed.

The same happened with other linux OS.

I could really appreciate your help

Thanks

---

### Post by yancek on 2014-07-24
How many windows partitions do you have on the disk and what is their size?  Are they taking up the entire disk?  Boot the Ubuntu flash drive and open a terminal and run this command to get info:  sudo fdisk -l(Lower Case Letter L in the command)  Post it here.  If your windows partition take up the entire disk then you can resize(shrink) one of the partitions from windows.

---

### Post by luismiguelmalmeida on 2014-07-24
I have 2 partitions and Yeah I shrank windows size to 160gb out of 500 gb

---

### Post by luismiguelmalmeida on 2014-07-24
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8e92c3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   337285119   168539136    7  HPFS/NTFS/exFAT
/dev/sda3       337287105   976766975   319739935+   f  W95 Ext'd (LBA)
/dev/sda5       337287168   976766975   319739904   83  Linux

Disk /dev/sdb: 16.2 GB, 16240345088 bytes
2 heads, 1 sectors/track, 15859712 cylinders, total 31719424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         232    31719423    15859596    b  W95 FAT32

---

### Post by oldfred on 2014-07-24
Was drive previously gpt partitioned? Or Windows 8?

It says it still has gpt info, but you have MBR(msdos) partitioning.
Windows DVD only installs in BIOS boot mode and converts drive to MBR, but leaves backup gpt partition table. 
Linux then sees MBR and gpt and assumes you want to totally erase disk to correct it and does not see Windows.

Best to remove backup gpt partition table.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by luismiguelmalmeida on 2014-07-25
I can't seem to know how to convert fully to MBR using fixparts

---

