---
title: "Swap partition not accessable"
date: 2007-09-09
forum: General Help
---

### Post by Palypup on 2007-09-09
Freezing while playing Nexuiz made me search to find the reason.
My install is spread across three hard drives, two of which have
swap partitions, 500 Mb on hda and 800 on hdd. The 800 Mb created
during the current install shows up using Disk Manager, fdisk, and
GParted but not accessable. But cat /proc/swaps shows that only the
500 Mb swap partition from a previous install is the only one in use.
The 800 Mb swap is listed in /etc/fstab and disk manager as hdd7,
but in fdisk -l and GParted, it shows up as hdd6.
I have tried to activate the 800 Mb swap which is not activated, to
no avail. I have reformated it, but did not delete and recreate.
After running cfdisk I get: FATAL ERROR: Bad logical partition: enlarged
logical partitions overlap. Hdd has, at the beginning, Ubuntu, then the
swap drive, followed by two fat32 storage partitions. Data has been lost
from the last of the fat32 partitions, but not recently.
Three drives each boot from bios, so technically is not a dual boot system.
Current operational swap is on hda, home is on hdb, and Ubuntu and 800 Mb
swap is on hdd. Anyone got any ideas short of a complete remodeling of the drive
with the faulty swap and the overlapping partitions? The other two OS's
access the two fat files on this drive without a problem and it is a 200 Gig
drive so am not looking foreward to moving all that data somewhere else just
to reclaim a swap drive.

---

### Post by Ozeuss on 2007-09-09
could you post relevant fstab and fdisk so we'll have a better view of your layout?

---

### Post by Palypup on 2007-09-09
Here she be.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd7       none            swap    sw              0       0
/dev/hdb5       /home           ext3    nodev,nosuid    0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /windows        ntfs    defaults        0       0
/dev/hda1       /fat_files      vfat    defaults        0       0
/dev/hda5       /fat_files      vfat    defaults        0       0
/dev/hdd5       /fat_files      vfat    defaults        0       0
/dev/hdd6       /fat_files      vfat    defaults        0       0
/dev/hda3       /Lin            ext3    defaults        0       0
/dev/hda4       none            swap    sw              0       0


bill@Ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4567    36684396    c  W95 FAT32 (LBA)
/dev/hda2            4568       11524    55882102+   f  W95 Ext'd (LBA)
/dev/hda3           11525       14529    24137662+  83  Linux
/dev/hda4           14530       14593      514080   82  Linux swap / Solaris
/dev/hda5            4568       11524    55882071    b  W95 FAT32

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10200    81931468+   7  HPFS/NTFS
/dev/hdb2           10201       14593    35286772+   f  W95 Ext'd (LBA)
/dev/hdb5           10201       14593    35286741   83  Linux

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1            2438       24792   179566537+   f  W95 Ext'd (LBA)
/dev/hdd2   *           1        2437    19575171   83  Linux
/dev/hdd5            2546       13668    89345466    b  W95 FAT32
/dev/hdd6            2438        2545      867447   82  Linux swap / Solaris
/dev/hdd7           13669       24792    89353498+   b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

---

### Post by Ozeuss on 2007-09-10
did you try to change your fstab to point to the second swap to hdd6? fdisk and gparted should show the "correct" location. change your fstab and then remount. see if that helps.

---

