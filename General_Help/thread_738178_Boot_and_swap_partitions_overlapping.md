---
title: "Boot and swap partitions overlapping"
date: 2008-03-28
forum: General Help
---

### Post by mferrier on 2008-03-28
Howdy,

I currently am running Gutsy dualbooting with Windows XP. One of the "26 boots without a fsck!" fscks seems to have screwed up my partition table but good. sda1 is my boot partition, sda5 is my swap, and they seem to be overlapping, according to fdisk:

```
$ sudo fdisk -l /dev/sda1

Disk /dev/sda1: 2683 MB, 2683305984 bytes
255 heads, 63 sectors/track, 326 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?       48437      119493   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(48436, 183, 40)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(119492, 104, 7)
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?       10501      131013   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(10500, 111, 30)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(131012, 158, 28)
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?      116395      236907   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(116394, 188, 12)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(236906, 234, 25)
Partition 3 does not end on cylinder boundary.
/dev/sda1p4   ?      179626      179629       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(179625, 87, 47)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(179628, 203, 42)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=385478656, size=  5240832, Id= c
/dev/sda2 : start=   160650, size=231560910, Id= 7, bootable
/dev/sda3 : start=231721560, size=152424720, Id=83
/dev/sda4 : start=384146280, size=  6570585, Id= 5
/dev/sda5 : start=384146343, size=  6570522, Id=82

```

Linux boots and runs fine, Windows seems to be running extremely slow, I assume due to it being confused about the partition table. When I load GParted up, it shows the entire disk as unallocated:

[IMG]http://img152.imageshack.us/img152/2319/gpartedyu8.png[/IMG]

fsck.msdos doesn't help either:

```
$ sudo fsck.msdos /dev/sda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  29:f0/08, 30:f9/00, 31:16/00, 65:01/00, 71:44/4e, 72:65/4f, 73:6c/20
  , 74:6c/4e, 75:4d/41, 76:44/4d, 77:33/45, 78:70/20, 79:6c/20, 80:61/20
  , 81:79/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Both FATs appear to be corrupt. Giving up.

$ sudo fsck.msdos /dev/sda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  29:f0/08, 30:f9/00, 31:16/00, 65:01/00, 71:44/4e, 72:65/4f, 73:6c/20
  , 74:6c/4e, 75:4d/41, 76:44/4d, 77:33/45, 78:70/20, 79:6c/20, 80:61/20
  , 81:79/20
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
Both FATs appear to be corrupt. Giving up.

```

Corrupt entries in my boot partition. Oy gevalt! So, my first instinct is to just delete the swap partition's entry and then hopefully GParted will run again. Is this a good idea?

Needless to say, I've backed up everything important on this drive... I'd just really not enjoy reinstalling everything again. 

Any advice anyone? Thanks in advance.

---

### Post by housam on 2008-03-28
check [[COLOR="Red"]_this guide_[/COLOR]]("http://www.linux.com/base/ldp/howto/Partition/recovering.html"), it may help

---

### Post by mferrier on 2008-03-28
Unfortunately that guide assumes ext2/3 filesystems. The partitions I'm working with are FAT32 and Linux Swap.

---

### Post by mferrier on 2008-03-28
Bump! I'm just kinda looking for a yea or nay about whether Ubuntu minds if you delete the swap partition.

---

### Post by seeker1458 on 2008-03-28
I know you can run ubuntu w/o a swap. Actually I run w/o a swap on my macbook.  But honestly I don't see what it would hurt? I mean your swap is cleared after every restart right?  And all it does is cache stuff when you RAM is low.  But...Im no expert...like I said I don't use a swap.

---

### Post by housam on 2008-03-30
You need the swap when downloading / installing updates, hypernating and also when playing some games - evev if you have enough RAM. 
you can reed about swap[[COLOR="Red"]_ here_[/COLOR]]("http://www.linux.com/base/ldp/howto/Partition/partition-types.html#swap-partitions").

---

