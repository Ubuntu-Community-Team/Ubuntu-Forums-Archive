---
title: "gparted doesn't see the partitions of my USB"
date: 2017-07-12
forum: General Help
---

### Post by bjlockie on 2017-07-12
gparted works for all my drives except my USB flash drive (it sees my USB hard drive).
It says "unknown" for the filesystem.
gksudo gparted /dev/sde1 sees my Windows partition and gksudo gparted /dev/sde2 see the ext2 partition.
gksudo gparted /dev/sde sees the size but no partitions.

gparted 0.25.0

---

### Post by Autodave on 2017-07-13
Perhaps the flash drive has failed? Have you tried it on another machine to confirm that it is working properly?

---

### Post by bjlockie on 2017-07-13
I can read and write to the filesystems on this machine, it is just gparted that doesn't see them.

$ sudo fdisk /dev/sde

Welcome to fdisk (util-linux 2.29).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): p
Disk /dev/sde: 14.7 GiB, 15804137472 bytes, 30867456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6f20736b

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sde1           2048 12584959 12582912    6G  b W95 FAT32
/dev/sde2       12584960 30867455 18282496  8.7G 83 Linux

---

### Post by efflandt on 2017-07-13
What is on your sde? If you booted from that, you definitely cannot change partitions on it from there. If it was an iso file written to that device, you probably cannot change partitions on it, but you should be able to create a new partition table on it and then create partition(s).

---

### Post by bjlockie on 2017-07-14
It is just a USB flash drive, I don't boot from it.
I'm trying to avoid deleting the partitions just so I can resize the partitions (that seems overkill).

---

