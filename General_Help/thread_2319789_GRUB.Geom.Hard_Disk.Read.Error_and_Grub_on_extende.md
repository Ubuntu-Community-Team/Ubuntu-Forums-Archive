---
title: "GRUB.Geom.Hard Disk.Read.Error and Grub on extended partition! How to fix?"
date: 2016-04-07
forum: General Help
---

### Post by siggi2 on 2016-04-07
Hi,

my system seems to be ok, yet Boot-Repair tells me, I have Grub on the extended partition, and ```
sudo dd if=/dev/sda bs=512  count=1 | hexdump -C
``` tells me: ```
GRUB .Geom.Hard Disk.Read. Error
```. Is this critical?

Details
********
Samsung Notebook NP300E5C, 500 GB HD, Multiboot Windows10, Ubuntu 1404.4, Debian Jessie, Xenial Xerus (Development).
_fdisk -l:_
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x19c4ca42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   197330943    98664448    7  HPFS/NTFS/exFAT
/dev/sda2       197330944   376979381    89824219   83  Linux
/dev/sda3       376979456   392722431     7871488   82  Linux swap / Solaris
/dev/sda4       392724478   976769026   292022274+   5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       392724480   874377215   240826368    7  HPFS/NTFS/exFAT
/dev/sda6       874379264   933763071    29691904   83  Linux
/dev/sda7       933765120   976769026    21501953+  83  Linux
```

I always have done within my installed Ubuntu 14.04
```
sudo grub-install /dev/sda
sudo grub-install --recheck /dev/sda
sudo update-grub
```
After a new install. A Grub in exrended parttion must have been left after some heedless tinkering with Centos, Scientific OS, OpenSuse? 

Should I be worried about the error message and the "dead" Grub on the extended partition?

Thanks.

siggi

---

### Post by oldfred on 2016-04-07
I think your dd is extracting the error messages that grub would use if it found issues.

But grub does not like to install to PBR - partition boot sectors. It has to convert to blocklists or hard coded addresses. If address of any part of grub changes due to a file update or even fsck then grub fails & you have to reinstall grub. 
And you cannot boot using PBR unless you have another grub chainloading to it.

---

### Post by siggi2 on 2016-04-07
Thanks, but I forgot to tell: I boot with MBR/MSDOS not with UEFI!

---

### Post by oldfred on 2016-04-07
Only BIOS installs use MBR & PBR(not recommended).
Perhaps one of your installs did use a PBR?
 
MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) 


Windows normally uses a PBR for added boot code. It boots from MBR to PBR. When grub chainloads to Windows it is just jumping to NTFS partitions PBR directly.

UEFI only uses the ESP - efi system partition which is a FAT32 formatted partition with boot flag.

---

### Post by siggi2 on 2016-04-09
@oldfres:

When I will be doing a future partitioning and installs, how can I avoid this
> Partition 4 (*the extended*) does not start on physical sector boundary.?

I.e., how can I calculate the correct sizes before partitioning with gparted?

---

### Post by oldfred on 2016-04-09
Extended partition does not matter. You do not directly write into extended partition, just the logicals inside the extended.
If not dual booting with Windows you can also use gpt partitioning with Ubuntu in BIOS or UEFI boot mode. 
Windows only boots with UEFI from gpt, so you have to have newer system or separate MBR drive for Windows if BIOS system. 
I have used gpt since about 10.10 for BIOS and with new system in UEFI which defaults to gpt. But then my XP was on a separate MBR partitioned drive.

       Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
sudo parted /dev/sda unit s print 


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

