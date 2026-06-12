---
title: "Recover NTFS partition deleted by Windows *8 upgrade"
date: 2013-01-14
forum: General Help
---

### Post by pssturges on 2013-01-14
Hi,

I have an XP/Mythbuntu desktop dual boot system. Additionally there is an NTFS partition that I used to store media & documents available to both installations.

Today I purchased and downloaded the Windows 8 Upgrade. Prior to running the upgrade, I backed up everything I needed on the XP partition to this other NTFS partition. I had a few failed attempts at the upgrade, but then once successful I was horrified to find that the upgrade had somehow deleted the partition with all my backups on it! The space is still there and is showing as unallocated, so I'm sure my data is still there.

I have tried the guides laid out [HERE]("https://help.ubuntu.com/community/DataRecovery#Lost_Partition") without any success. Some because I'm not quite sure how to use, others such as parted, seem to run correctly, but don't seem to actually change anything.

So next I tried [THIS]("http://ubuntuforums.org/showthread.php?t=1192598") guide to use fsdisk simply edit the partition table. It seems quite straight forward to do what needs doing to fix the problem, but I always seem to end up with an invalid partition table, that gaparted at least can't read.

So my partition table currently looks like this:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=640029537, Id= 7, bootable
/dev/sda2 : start=640029600, size=1313490465, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=1936523295, size= 16161390, Id=83
/dev/sda6 : start=1952684748, size=   835317, Id=82
```

The screen shot attached makes it fairly obvious where my NTFS partition was.

So I tried editing the partition table like so (and a few variations):
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=640029537, Id= 7, bootable
/dev/sda2 : start=640029600, size=1313490465, Id= 5
/dev/sda3 : start=640029600, size=1296493695, Id= 7
/dev/sda4 : start=        0, size=         0, Id= 0
/dev/sda5 : start=1936523295, size= 16161390, Id=83
/dev/sda6 : start=1952684748, size=   835317, Id=82
```

But as I say, this keeps giving me an invalid partition table. Any ideas where I'm going wrong.

Any help appreciated,

Thanks
Phil

---

### Post by oldfred on 2013-01-14
I know this is one of the rules.

> To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
    

So maybe you should leave one sector at the beginning? Mine shows 2.
```
fred@A105-Precise:~$ sudo sfdisk -l -uS

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 113595614  113595552   7  HPFS/NTFS/exFAT
/dev/sda2     113595615 175028174   61432560   7  HPFS/NTFS/exFAT
/dev/sda3     175028236 312062624  137034389   5  Extended
/dev/sda4             0         -          0   0  Empty
/dev/sda5     175028238 205744454   30716217  83  Linux
/dev/sda6     205744518 211881284    6136767  82  Linux swap / Solaris
/dev/sda7     211881348 312062624  100181277  83  Linux


```

Did you backup partition table first?
       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt


I have never done it, but some posts by those who know a lot more.
       
 Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

