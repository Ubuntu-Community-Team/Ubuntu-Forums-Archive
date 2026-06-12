---
title: "Hard drives and mounting (handed down pc)"
date: 2016-10-20
forum: General Help
---

### Post by xfearxnxloathing on 2016-10-20
Two screenshots of the extra drives not mounted (ignore the 1TB and the Kingston). 
One seems to have another OS Install on it and is mounted for whatever reason but with two other partitions, neither are mounted. The other drive doesn't seem to have anything on it and also isn't mounted. The hard drive with three partitions has some sort of error that I would like to fix if possible and then I would like to mount both drives/all partitions. I'm hoping someone can help me out and explain step by step. Also, I have included the readout from the .*sudo fdisk -l* command.

[ATTACH=CONFIG]271700[/ATTACH]
[ATTACH=CONFIG]271701[/ATTACH]

```
Disk /dev/sda: 186.3 GiB, 200049647616 bytes, 390721968 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000cfee4


Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    499711    497664   243M 83 Linux
/dev/sda2       501758 390721535 390219778 186.1G  5 Extended
/dev/sda5       501760 390721535 390219776 186.1G 8e Linux LVM


GPT PMBR size mismatch (625142447 != 624093871) will be corrected by w(rite).


Disk /dev/sdb: 297.6 GiB, 319536062464 bytes, 624093872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1           1 625142447 625142447 298.1G ee GPT


Disk /dev/mapper/ubuntu--vg-root: 182.1 GiB, 195496509440 bytes, 381829120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/ubuntu--vg-swap_1: 4 GiB, 4294967296 bytes, 8388608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdc: 931.5 GiB, 1000170586112 bytes, 1953458176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00023f15


Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        2048 1953458175 1953456128 931.5G  7 HPFS/NTFS/exFAT


Disk /dev/sdd: 28.9 GiB, 30966546432 bytes, 60481536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x274c2d6a


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdd1  *       63 60452594 60452532 28.8G  c W95 FAT32 (LBA)



```

---

### Post by TheFu on 2016-10-21
fdisk doesn't work with GPT disks. Use **parted** instead.  gparted is the GUI version, but for posting here use **sudo parted -l**.  I appreciate the code tags. Thanks.

The other disk is using LVM, so things are a little more complicated and much, much, much more flexible to an expert.  You'll need to know about the logical volumes, volume groups and physical extents .... **lvs**, vgs, pvs will show those.  Basically, I think of LVs as really, really, really, smart partitions that can be resized up/down on a running system.

The **lsblk** command will show how things are setup too. It is a nice overview and often has enough detail to be useful.

As for permanently mounting different partitions and LVs, you'll want to modify the /etc/fstab.  Google will find a how-to.Use "ubuntu fstab" as the search.

---

### Post by Impavidus on 2016-10-21
Your /dev/sda1 looks like a /boot partition, with the unencrypted part of the OS. You need that if you use an LVM/encrypted system. /dev/sda2 is an extended partition, which doesn't contain a file system and therefore cannot be mounted. It contains logical partitions, in this case only /dev/sda5. /dev/sda5 is another container, containing /dev/ubuntu-vg/root and /dev/ubuntu-vg/swap. These are LVM volumes, a flexible kind of partition often used to enable encryption.

/dev/sda says the self test failed. I can't say why, but this suggests it may be close to hardware failure. Or it may be a false warning. Check smart status or details of self test for more info. You can hope the disk will last for a while, but make sure you've got good backups. You should have good backups anyway.

---

### Post by xfearxnxloathing on 2016-10-23
Thanks guys! I'll look into everything and report back if I have any questions, I'm sure I will lol.

---

### Post by xfearxnxloathing on 2017-01-07
> **TheFu said:**
> fdisk doesn't work with GPT disks. Use **parted** instead.  gparted is the GUI version, but for posting here use **sudo parted -l**.  I appreciate the code tags. Thanks.

The other disk is using LVM, so things are a little more complicated and much, much, much more flexible to an expert.  You'll need to know about the logical volumes, volume groups and physical extents .... **lvs**, vgs, pvs will show those.  Basically, I think of LVs as really, really, really, smart partitions that can be resized up/down on a running system.

The **lsblk** command will show how things are setup too. It is a nice overview and often has enough detail to be useful.

As for permanently mounting different partitions and LVs, you'll want to modify the /etc/fstab.  Google will find a how-to.Use "ubuntu fstab" as the search.

When I open Gparted I get this ```
Invalid argument during seek for read on /dev/sdb
```

Is the drive a goner? Not sda but sdb, it's a 320 WD and the drive I am currently talking about.

---

### Post by xfearxnxloathing on 2017-01-07
***UPDATE***

So there wasn't a partition table on the drive and that is what Gparted was letting me know. I deleted it using Testdisk after finding out that it was an old Linux OS install and nothing important was on the drive. Anyway, after ignoring the message, I selected the drive from the drop down menu in the upper right corner and selected the drive, added a GPT partition table to it and then formatted the drive ext4. I'm hoping now I will be able to install to it.

---

