---
title: "gparted reports incorrect values"
date: 2008-03-19
forum: General Help
---

### Post by cvp on 2008-03-19
My previous setup (**320** GB SATA HD):
**60 GB** - NTFS - Windows XP Professional SP2
**59 GB** - ext3 - Ubuntu Linux 7.10
**1 GB** - linux-swap
**200 GB** - FAT32 - data shared between the two operating systems

I've been running low on disk space in general, so I dug up a 300 GB PATA harddrive I had laying around, and did the following:
*formatted the 300 GB drive as ext3
*copied over all contents of the 200 GB FAT32 partition, above, to this new drive
*used gparted to remove the 200 GB partition, move linux-swap so that there's 100 GB following it, move the 59 GB ext3 partition so that there's 100 GB total preceding it and expanded it to 99 GB, expanded the 60 GB NTFS partition to 100 GB
(before: [-60 GB NTFS-][-59 GB ext3-][-1 GB linux-swap-][-200 GB FAT32-]
after: [-100 GB NTFS-][-99 GB ext3-][-1 GB linux-swap-][-100 GB unallocated space-], plus a second 300 GB ext3 drive)
*I plan to format the 100 GB unallocated space to NTFS and install Windows Vista Business, for which I have been given a free license for being a computer science student at my university. I have not installed it yet, but I imagine a few more problems will arise in the process of doing so...

Problems:
**gparted** gave errors (I should've written them down) when it got to expanding the 60 GB NTFS partition to 100 GB, but things still seemed to work out fine... sort of.
Windows XP reports that its C drive is still 60 GB and has just as little much free space as it did before the expansion, etc.
Stranger still, both **Norton Partition Magic** and **gparted** report that that volume is in fact 100 GB in size and give an accurate number for disk space used, but the value for free disk space is the old value, before the volume was resized.

Results of **sudo fdisk -l**:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b377b37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12904   103651348+   7  HPFS/NTFS
/dev/sda2           12905       25961   104880352+  83  Linux
/dev/sda3           25962       26091     1044225   82  Linux swap / Solaris
/dev/sda4           26092       38913   102992715    7  HPFS/NTFS

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a443a44

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666   83  Linux
```
That first NTFS volume is clearly 100 GB, and it ends just about where it should end if it were a 100 GB drive.

For now, this is really more of a mild annoyance since I don't have 100 GB to work with in Windows, though everything else still works fine (booting, accessing /dev/hdb1, etc.)

What I've tried:
I've had this problem in the past, and it was solved relatively simply by "refreshing the disk's memory," which consisted of making a minor adjustment to the problem partition's size and then resizing it again. This time, Partition Magic throws a few errors and immediately reboots, and gparted refuses to resize it.
I'm about to run CHKDSK before I run to class.

Any other suggestions?

Thanks in advance,
-cvp

---

### Post by cvp on 2008-03-20
For the record, CHKDSK fixed nothing. I didn't really think it would, anyway.

I also managed to install Vista quite painlessly, and am now tri-booting. The only issue left is convincing those parts of my HD that are reporting that its first partition is 60 GB that it's actually 100 GB.

At this point, I'd even be willing to completely copy over data from WinXP and reinstall. Does anyone at least know a good way of moving back all my settings without having to reinstall everything? I'd be willing to do just about anything short of **dd**'ing that portion of the disk to some blank region on my second hard drive, reformatting, and **dd**'ing back.

-cvp

---

