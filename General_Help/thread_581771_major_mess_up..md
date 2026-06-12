---
title: "major mess up."
date: 2007-10-19
forum: General Help
---

### Post by kadafi69 on 2007-10-19
Well, i decided to delete my windows partition, using the Partition Editor. I removed one partition and then Partition Manager closed, I re-opened it and all of my partitions have gone, there is just one large empty space. I darnt turn my PC off now just in case everything will be wiped. What can i do?

---

### Post by rossiFan on 2007-10-19
Go to a terminal and see if fdisk shows you the same thing.

---

### Post by kadafi69 on 2007-10-19
> fdisk /dev/hda

Unable to open /dev/hda
root@myles-XPC:~# fdisk /dev/sda8
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x84d74a17.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 1243.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): 
I dont really know what im doing, im quite new to linux.

---

### Post by dayvy on 2007-10-19
sudo fdisk -l

This will list your partitions.

---

### Post by Light- on 2007-10-19
It seems that by closing the partitioner halfway through partitioning, you have managed to corrupt your hard disk

---

### Post by kadafi69 on 2007-10-19
>  sudo fdisk -l

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1780177f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS


so if its become corrupt, im screwed right? anyway to fix it?

---

### Post by dayvy on 2007-10-19
type man fsck to see how you can repair. May or may not work. It won't work for your ntfs partition though. You'll have to use a checkdsk for that.

---

### Post by kadafi69 on 2007-10-19
Man fsck brings up a serious amount of reading, duno where to begin with it all. any ideas?

---

### Post by kadafi69 on 2007-10-21
bump

---

