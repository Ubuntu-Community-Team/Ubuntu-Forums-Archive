---
title: "Salvaging data form a damaged VM with the aid of a donor clone VM"
date: 2013-07-04
forum: General Help
---

### Post by fridgefreezer on 2013-07-04
Hi everyone. I'll try to cut a long story short here, I'm hoping someone can help me!

I have a Virtualbox machine running Ubuntu 12.04 with a 20Gb virtual drive. Thanks to a moment of inattention on my part, there was an attempt to format/re-partition /dev/sda (the boot/root drive) instead of the usb stick I was intending to target :oops:

Happily, I have a recent-ish clone of the virtual machine and the virtual drive, so I have almost everything (including an exact image of the drive geometry) apart from maybe a week's work - changes to a few source code files which I would like to get back. In terms of the contents of the drive, it's a few megabytes of files out of 20Gb - and the rest of it can be ignored. It does not need to be able to boot, I don't care about the OS files, everything like that can just be cloned from the backup.

Currently the original machine does not boot and has no partition table etc., giving the "1234F:" error [described in this thread]("http://ubuntuforums.org/showthread.php?t=859101").

I have cloned the partition table within PartedMagic like [this]("https://www.sharktooth.de/doku.php/linux:clone_disc_partition"), where **sda** is the cloned backup and **sdb** is the damaged original drive:

```
Welcome - Parted Magic (Linux 3.6.10-pmagic)

root@partedmagic:~# sfdisk -d /dev/sda > parts.txt
sfdisk: Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

root@partedmagic:~# cat parts.txt 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 39911424, Id=83, bootable
/dev/sda2 : start= 39915520, size=  1044480, Id= 5
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 39917568, size=  1040384, Id=82
root@partedmagic:~# sfdisk /dev/sdb < parts.txt 
Checking that no-one is using this disk right now ...
OK

Disk /dev/sdb: 2549 cylinders, 255 heads, 63 sectors/track
sfdisk: Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+   2484-   2485-  19955712   83  Linux
/dev/sdb2       2484+   2549      66-    524097    f  W95 Ext'd (LBA)
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5       2484+   2549      66-    524091   82  Linux swap
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *      2048  39913471   39911424  83  Linux
/dev/sdb2      39915520  40959999    1044480   5  Extended
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5      39917568  40957951    1040384  82  Linux swap
Warning: partition 1 does not end at a cylinder boundary
Warning: partition 2 does not start at a cylinder boundary
Warning: partition 2 does not end at a cylinder boundary
Warning: partition 5 does not end at a cylinder boundary
Successfully wrote the new partition table

Re-reading the partition table ...

```

Which puts the partitions back where they were, but the main partition /dev/sdb1 shows as unknown filesystem and recovery tools find no data on it :(

Is there some way of copying more than just the partition table (eg the filesystem, mbr, whatever?) but without over-writing the entire contents of the drive?
In olden days I'd say something like using a hex editor to clone the first N pages of data from the backup to the original drive, but I'm relatively unfamiliar with this *ux/ubuntu stuff and only hazily aware of things like Grub etc.

It feels like there should be some way to salvage a few files from this?

---

### Post by fridgefreezer on 2013-07-04
Just to drop an update in case it helps others - I'm getting somewhere using [Foremost]("http://foremost.sourceforge.net/") which basically trawls through the data looking for known filetypes/strings. A popular GUI-based alternative seems to be [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

