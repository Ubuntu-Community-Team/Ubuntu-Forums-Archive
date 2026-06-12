---
title: "Linux Partitions Issues"
date: 2013-06-25
forum: General Help
---

### Post by wmorrison1967 on 2013-06-25
Hello,
     I am a newbie to  linux and need some basic help with fdisk.  I have installed Linux and now  want to create some virtual drive on my partitioned hard drive.  When I  try to use fdisk I am getting no more sectors available on the 500 gig  hard disk.  This should not be the case since deliberately did not allocate all the space.

This is the result of fdisk -l:
 
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk identifier: 0x000372b3
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          64      512000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              64       60802   487873536   8e  Linux LVM
 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe37e2acd
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      119817   962423808    7  HPFS/NTFS
/dev/sda2          119817      121602    14336000    7  HPFS/NTFS
 
Disk /dev/mapper/vg_linux-lv_root: 53.7 GB, 53687091200 bytes

255 heads, 63 sectors/track, 6527 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
 
 
Disk /dev/mapper/vg_linux-lv_swap: 8371 MB, 8371830784 bytes

255 heads, 63 sectors/track, 1017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
 
 
Disk /dev/mapper/vg_linux-lv_home: 161.1 GB, 161061273600 bytes

255 heads, 63 sectors/track, 19581 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

---

### Post by MidnightGrey on 2013-06-25
> **wmorrison1967 said:**
> 

This is the result of fdisk -l:
 
Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, **60801 cylinders**
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk identifier: 0x000372b3
 
   Device Boot      Start         **End**      Blocks   Id  System
/dev/sdb1   *           1          64      512000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              64 **      60802**   487873536   8e  Linux LVM
 


Kinda tricky to read but it looks like you've used all your blocks.
You can open gparted which will give you a graphical visual of your partitions and show you any unallocated space you have available.
if you dont have gparted you can install it using this command:
[I]sudo apt-get install gparted
[/I]

---

### Post by wmorrison1967 on 2013-06-25
Thanks for the response.  Could I remove this partititon

Partition 1 does not end on cylinder boundary.
/dev/sdb2              64 **      60802**   487873536   8e  Linux LVM 

without causing an issue and then recreate it smaller?

---

### Post by wmorrison1967 on 2013-06-26
Solve the issue.  I needed to use the LV Manager functions.  Now I am set.  I use lvcreate with mkfs.xxxx to create the requisite virtual disks.

---

