---
title: "external harddrive permission"
date: 2007-01-12
forum: General Help
---

### Post by Lowfront on 2007-01-12
Alright now I just reformatted my external hard drive to ext 2 so I can write to it.  Now the problem is I don't have permission to write on it.  Any thoughts.  Its weird I have a couple seperate partitions on it.  And the one I need to use all the time isn't working.  

Could It be because I have a folder on my computer called Media, and that partition is called Media?

---

### Post by logos34 on 2007-01-12
Your fstab file will show what's going on.

Run these commands and post the output:

cat /etc/fstab

sudo fdisk -l

---

### Post by Lowfront on 2007-01-12
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bc2df370-4369-4f2d-9b7b-a50a9a3af0f2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=259c5485-3b2a-4f54-9e47-63fee085c495 /Media          ext3    defaults        0       2
# /dev/sda5
UUID=990c87ba-fbfe-447e-9a61-a3fe80f81165 /home           ext3    defaults        0       2
# /dev/sda7
UUID=35f580c8-5dd3-431e-9cc1-817b2eed21be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0





Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1276        2551    10246131   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            2551       12161    77195601+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            2551        6655    32961568+  83  Linux
/dev/sda6            6656       10760    32973381   83  Linux
/dev/sda7           10761       10887     1020096   82  Linux swap / Solaris
/dev/sda8           10888       12161    10233373+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26577   213479721   83  Linux
/dev/sdb2           26578       27585     8096760    c  W95 FAT32 (LBA)
/dev/sdb3           27586       30401    22619520    5  Extended
/dev/sdb5           27586       30401    22619488+  bc  Unknown

---

### Post by logos34 on 2007-01-12
> # /dev/sda6
UUID=259c5485-3b2a-4f54-9e47-63fee085c495 /Media ext3 defaults 0 2

this is the partition you can't access on the external?

wait, this is on the internal drive and the name of the mountpoint is conflicting with another '/Media' mountpoint for a partition on your external, right?

---

### Post by logos34 on 2007-01-12
what does 
> ls /Media

show?

---

### Post by Lowfront on 2007-01-12
Books  lost+found  Music  Psychology  To Harddrive  Video



thats my partition on the computer not the harddrive

---

### Post by logos34 on 2007-01-12
.

---

### Post by Lowfront on 2007-01-13
bump

---

### Post by marc_c on 2007-01-13
Is the problem that you can read the external harddrive but not write?  If that is the case, it is a permissions problem.  You can change those permissions via the chown command.

sudo chown -R username:groupname /media/externaldiskname

---

### Post by Lowfront on 2007-01-15
how do I know the external disk name?

---

### Post by Lowfront on 2007-01-16
bump

---

### Post by poulet on 2007-01-16
hello

---

### Post by Lowfront on 2007-01-18
.anyone?

---

### Post by altonbr on 2007-01-22
This is my "sudo fdisk -l" output:

> Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            5347       30394   201198060    f  W95 Ext'd (LBA)
/dev/sda3            1217        5346    33174225    b  W95 FAT32
/dev/sda5            5347       26240   167831023+   b  W95 FAT32
/dev/sda6           26241       26371     1052226   82  Linux swap / Solaris
/dev/sda7           26372       30394    32314716   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS


Notice how /dev/sdb1 (or /media/USB Drive/) is NTFS? You can't write to NTFS by default. Are you having the same problem? You need to format it to a usable filesystem or install NTFS write support.

---

