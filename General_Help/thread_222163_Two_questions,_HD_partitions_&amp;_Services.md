---
title: "Two questions, HD partitions &amp; Services"
date: 2006-07-24
forum: General Help
---

### Post by Prism on 2006-07-24
Hi there,

I have two (unrelated) questions about partitioning my HD and about speeding up my PC by disabling unneeded services:

1. I have a 80 GB HD, and I have 4 partitions on it: 14.65 GB FAT32 partition for WinXP, 21 GB Ext3 partition for my Ubuntu Dapper, a swap partition (1.5 gigs) and a 30 gigs FAT32 partition for folders etc.
I saved an unpartitioned space (about 10 GB) for a later time, and this time has come now :). How can I partition this space as well? I remember I tried to do it before but couldn't because theree's a limitation on the partitions number, but surely there's something I missed.

2. My Ubuntu machine boots up really slow, and I'd like to reduce the booting time. IMHO it can be done if I disable unneeded services at startup, but I'm not sure what I can remove without damaging the system. The services in question are:

[LIST]
[*]hplip: HP Printing and Imaging System - I have a Canon printer. Does Ubuntu still need this service?
[*]laptop-mode; hotkey-setup: Auto-configures laptop hotkeys; apmd: Monitors battery status for some older laptops - I don't even own a laptop :-k 
[*]rsync - I don't think I've ever used it. No daily backups here. Can I disable this?
[*]bluez-utils: Bluetooth services - I've got no bluetooth devices. :( 
[*]mdadm: Manages multiple disk devices for fault-tolerance - what is that anyway?
[*]anacron; cron - I've never used cron tasks. Does Ubuntu use any?
[*]atd: Enables scheduling of jobs - Does it have anything to do with cron?
[/LIST]

What can I disable from the list above? What should I leave if I don't want unexpected "brown screens of death"?

Thanks in advance!

---

### Post by joft on 2006-07-24
> **Prism said:**
> 
1. I have a 80 GB HD, and I have 4 partitions on it: 14.65 GB FAT32 partition for WinXP, 21 GB Ext3 partition for my Ubuntu Dapper, a swap partition (1.5 gigs) and a 30 gigs FAT32 partition for folders etc.
I saved an unpartitioned space (about 10 GB) for a later time, and this time has come now :). How can I partition this space as well? I remember I tried to do it before but couldn't because theree's a limitation on the partitions number, but surely there's something I missed.


So you already have 4 partitions. Now the question is, are they all of type "primary"? If that's the case, then you won't be able to use the unpartitioned space, because the rule is, that you can only have 4 primary partitions per harddisk. Though you can have more by using another method: you can have 3 primary and 1 "extended" partition. Think of extended partitions as containers for a number of "logical" partitions.

So, if you have an extended partition, this partition has to be the last one being in front of the unpartitioned space, so the partition will be able to resize the extended partitioning tool and create a new 10GB logical partition at the end.
If that is not the case (extended being the last one), again there is nothing you can do - you have to repartition - which means, that you have to move/delete some partition (you may wnat to look at gparted for that, gparted can be downloaded with a bootable rescue system).

> **Prism said:**
> 
[LIST]
[*]hplip: HP Printing and Imaging System - I have a Canon printer. Does Ubuntu still need this service?
[*]laptop-mode; hotkey-setup: Auto-configures laptop hotkeys; apmd: Monitors battery status for some older laptops - I don't even own a laptop :-k 
[*]rsync - I don't think I've ever used it. No daily backups here. Can I disable this?
[*]bluez-utils: Bluetooth services - I've got no bluetooth devices. :( 
[*]mdadm: Manages multiple disk devices for fault-tolerance - what is that anyway?
[*]anacron; cron - I've never used cron tasks. Does Ubuntu use any?
[*]atd: Enables scheduling of jobs - Does it have anything to do with cron?
[/LIST]


I can't tell you something for each one, just the ones I know:
[LIST]
[*]laptop-mode, hotkey-setup: AFAIK should be save to deactivate
[*]rsync: AFAIK should be save to deactivate
[*]bluez-utils: save to deactivate, uninstall package bluez-*
[*]mdadm: save to deactivate, uninstall package mdadm
[*]anacron, cron: Ubuntu uses cron, I would leave this alone
[/LIST]

---

### Post by Prism on 2006-07-25
Let's see. The partitions in my computer are sorted like this:
Partition 1 - WinXP FAT32
Partition 2 - Ubuntu Ext3
Swap Partition
Partition 4 - Documents FAT32

Can I convert partition 4 to an extended partition? Actually, in second thought, I'd rather resize partition 4 so it'll be 40 GB, without any additional partition. Can it be done?


Thanks for your reply!

---

### Post by joft on 2006-07-25
> **Prism said:**
> 
Partition 1 - WinXP FAT32
Partition 2 - Ubuntu Ext3
Swap Partition
Partition 4 - Documents FAT32


Sorry, but this doesn't say anything about the existence of an extended partition. You can call:
```

sudo sfdisk -l /dev/hda

```
which will list (=> -l) your partition table(s). You might have to replace the device name in the above call (first IDE disk "hda", first SCSI or SATA disk "sda").

> **Prism said:**
> 
Can I convert partition 4 to an extended partition?


Well, I never did that - and atm I can't think of a partitioner which is able to do this (if partition 4 is a primary one). Removing partition 4, creating an extended partition and 2 logical in there seems to be a solution - but then you would have to make a backup of partition 4 ......

> **Prism said:**
> 
Actually, in second thought, I'd rather resize partition 4 so it'll be 40 GB, without any additional partition. Can it be done?


Yes. Any FAT resizing tool should do it - e.g. gparted or of course well know commercial software.

---

### Post by Prism on 2006-07-25
Thanks for your help. I've resized the partition and got 10 more GB for storage. Thanks! :)

---

