---
title: "reinstalling ubuntu in its own partiton"
date: 2008-05-17
forum: General Help
---

### Post by Wartender on 2008-05-17
i recently installed ubuntu as a dual boot with windows XP in my eMachines T5046... and then hopelessly messed it up trying to get desktop effects to work. if don't have any data in ubuntu so i don't mind losing all the files IN UBUNTU (i don't want to get near messing with windows while doing this). can i reinstall ubuntu (7.10) in the partition i made for it in the first place without touching windows at all? i have the live CD of 7.10 and everything.
and btw if i need to actually use ubuntu in the process i only have recovery available.

---

### Post by housam on 2008-05-17
Yes you can . and can be done by choosing the manual partitioning. we will not make any new partitions but this is necessary to assign the ubuntu partition again . to know which partition was for ubuntu ,Insert the live cd and type in a terminal 
```
sudo fdisk -l
```
where -l is a small L and post the result

---

### Post by Wartender on 2008-05-17
so i out in the live CD and boot from it (with safe graphics mode because the other mode doesn't work :\) go to the terminal and type that?

---

### Post by Wartender on 2008-05-17
this is what i get
```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2eb22eb1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         594       13954   107322232+   7  HPFS/NTFS
/dev/hda2               1         593     4763241    b  W95 FAT32
/dev/hda3           13955       23991    80622202+  83  Linux
/dev/hda4           23992       24321     2650725    5  Extended
/dev/hda5           23992       24321     2650693+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 1052 MB, 1052770304 bytes
2 heads, 63 sectors/track, 16318 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x00809e06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16319     1028080    6  FAT16

```
now what do i do? i don't recognize any of this or what i should put in the manual partition thingy.

---

### Post by housam on 2008-05-17
the partition hda3 is your Ubuntu  partition( EXT3 FORMAT ). so you can assign this one as a root partition for Ubuntu with the sign (/).

---

