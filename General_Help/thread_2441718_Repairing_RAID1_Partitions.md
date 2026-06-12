---
title: "Repairing RAID1 Partitions"
date: 2020-04-26
forum: General Help
---

### Post by giobaxx on 2020-04-26
I need some help because I will have to replace a disk in a Linux Workstation and rebuild its Software Raid1  For Sure before start I will run a full data backup but I never did so I need to be sure about the step I need to follow. The system should be configured like below, could you tell me if the procedure below is correct or no?

> md0  /dev/sda1  +  /dev/sdb1   where is mounted the Swap Partition
md1  /dev/sda2  + /dev/sdb2   where is mounted the / Partition 
md2  /dev/sda3  +  /dev/sdb3   where is mounted the Swap Partition

I have sda2 that is marked as failed I have to replace I need to mark all the partition /dev/sdb as failed 

> mdadm --manage /dev/md0 --fail /dev/sdb1
mdadm --manage /dev/md1 --fail /dev/sdb2
mdadm --manage /dev/md2 --fail /dev/sdb3


then I will remove all the partition from the raid:

> mdadm --manage /dev/md0 --remove /dev/sdb1
mdadm --manage /dev/md1 --remove /dev/sdb2
mdadm --manage /dev/md2 –remove  /dev/sdb3


Then I shut down  the system and I will replace the disk where I have to create the same partition type I have in sda

> sfdisk -d /dev/sda | sfdisk /dev/sdb

and then I will add the  partition to the raid system
 
> mdadm --manage /dev/md0 --add /dev/sdb1
mdadm --manage /dev/md1 --add /dev/sdb2
mdadm --manage /dev/md2 –add  /dev/sdb3

Is it correct what I wrote? I hope yes,  but now what it make me more concerned if the RAID software needs boot in UEFI mode. If I remember well in this case I should have a standard Partition /boot/efi and I should have a situation like this

> /dev/sda1                                Where is Mounted /boot/efi
md0  /dev/sda2  +  /dev/sdb2   Where is mounted the Swap Partition
md1  /dev/sda3  + /dev/sdb3    Where is mounted / 
md2  /dev/sda4  +  /dev/sdb4   Where is mounted /Home


Now If the broken disk were sda we need to repair not only the Raid partitions but   also reinstall the /dev/sda1 with the efi partition to make the system bootable again. In this case there is a way to proceed? or maybe it's easier to backup  the system and rebuilt?

Thanks in advance for any help.

---

