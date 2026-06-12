---
title: "After partition resize, i get error &quot;Can't have a partition outside the disk!&quot;"
date: 2014-07-25
forum: General Help
---

### Post by ramidavis2 on 2014-07-25
Help!
I used Easeus partition manager in windows 7 to change size of my win7 partition. I was going to give the extra space to my Ubuntu install.
Easeus said it needed to shutdown and perform the resize on next boot, so i shut down, selected windows 7 from grub, and let it work.
After completing the resize, it shut down my computer, as normal. When i turned it back on, i was at a grub rescue prompt.

Thankfully, i had a live USB stick of ubuntu with boot repair installed to it.
I booted to this, and used boot repair, which worked to get my grub back successfully.
I rebooted from the live USB, picked ubuntu from grub, and thought everything was OK.... Until i fired up GParted.
It claims my HDD is 100% unallocated space.
Right clicking the unallocated space, i see the error "can't have a partition outside disk!" ...

I powered down, and picked windows 7 from grub. It boots perfectly.
Easeus is showing all my partitions. windows disk utility is showing my partitions.
I have installed in windows 7 a program/driver called ext2-fsd which allows me to mount my linux partitions.
This program is still able to allow me to mount my linux partition.

Apearently, i have botched up the mbr.

I reboot into linux, and i have issued the folling in a terminal:
~$ parted -l
Error: Can't have a partition outside the disk!                           

~$ fdisk -l
Error: Can't have a partition outside the disk!

~$ gfdisk -l /dev/sda
GNU Fdisk 1.2.4
Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

Error: Can't have a partition outside the disk!                           
~$ sfdisk -l

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  41617   41618- 334296553+   7  HPFS/NTFS
/dev/sda2      44661+  46574-   1913-  15358976   83  Linux
/dev/sda3      46574+  60546-  13973- 112232420   83  Linux
/dev/sda4      60546+  60801     256-   2053516+   f  W95 Ext'd (LBA)
/dev/sda5      60546+  60801-    255-   2046968   82  Linux swap / Solaris

~$ cd Desktop;sudo testdisk /log
 
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
TestDisk exited normally.

~/Desktop$ sudo sfdisk -d
[sudo] password for a: 
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=668593107, Id= 7, bootable
/dev/sda2 : start=717494272, size= 30717952, Id=83
/dev/sda3 : start=748212224, size=224464840, Id=83
/dev/sda4 : start=972677097, size=  4107033, Id= f
/dev/sda5 : start=972679168, size=  4093936, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=  7851969, Id= b, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

~/Desktop$ dd if=/dev/sda of=sda-ahcomput.mbr bs=512 count=1
1+0 records in
1+0 records out
512 bytes (512 B) copied, 6.1181e-05 s, 8.4 MB/s
--------
In testdisk, i allowed it to scan, and backed it up to "backup.log", and then quit.
Attached is my backup.log and testdisk.log, and sda-ahcomput.mbr , contained in help.tar.bz2

backup.log:
```
#1406319528 Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
 1 : start=       63, size=668593107, Id=07, *
 2 : start=717494272, size= 30717952, Id=83, P
 3 : start=748212224, size=224464840, Id=83, P
 4 : start=972677097, size=  4107033, Id=0F, E
 5 : start=972679168, size=  4093936, Id=82, L

```
testdisk.log:
```
Using locale 'en_US.UTF-8'.


Fri Jul 25 15:18:27 2014
Command line: TestDisk /log

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.38-16-generic-pae (#67-Ubuntu SMP Thu Sep 6 18:18:02 UTC 2012)
Compiler: GCC 4.5 - Oct 17 2010 20:12:36
ext2fs lib: 1.41.14, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, LBA48, DCO support
/dev/sda: size       976773168 sectors
/dev/sda: user_max   976773168 sectors
/dev/sda: dco        976773168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA ST9500325AS

Partition table type (auto): Intel
/dev/sda: Device Configuration Overlay (DCO) present.
Disk /dev/sda - 500 GB / 465 GiB - ATA ST9500325AS
Partition table type: Intel

Analyse Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Geometry from i386 MBR: head=255 sector=63
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
Current partition structure:
 1 * HPFS - NTFS              0   1  1 41617 254 63  668593107 [windows 7]
 2 P Linux                44661 242 62 46574  14 32   30717952 [zorin os 8]
 3 P Linux                46574  14 33 60546  88 30  224464840 [ubuntu]
 4 E extended LBA         60546  89  1 60801 254 63    4107033
 5 L Linux Swap           60546 121 56 60801  79 62    4093936
Backup partition structure
Computes LBA from CHS for Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     HPFS - NTFS              0   1  1 41617 254 63  668593107 [windows 7]
     NTFS, 342 GB / 318 GiB
     Linux                44661 242 62 46574  14 32   30717952 [zorin os 8]
     EXT3 Large file Sparse superblock, 15 GB / 14 GiB
     Linux                46574  14 33 60546  88 30  224464840 [ubuntu]
     EXT3 Large file Sparse superblock Recover, 114 GB / 107 GiB
     Linux Swap           60546 121 56 60801  79 62    4093936
     SWAP2 version 1, 2096 MB / 1998 MiB
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2

interface_write()
 1 * HPFS - NTFS              0   1  1 41617 254 63  668593107 [windows 7]
 2 P Linux                44661 242 62 46574  14 32   30717952 [zorin os 8]
 3 P Linux                46574  14 33 60546  88 30  224464840 [ubuntu]
 4 E extended LBA         60546  89  1 60801 254 63    4107033
 5 L Linux Swap           60546 121 56 60801  79 62    4093936
simulate write!

TestDisk exited normally.
```

---

### Post by coffeecat on 2014-07-25
The one needed piece of information you haven't given is the **full** output of "sudo fdisk -l". You've only given us one line. And you need to use sudo. The output of sfdisk is no use because it is given in cylinders. We need sector output which "sudo fdisk -l" will give us.

If the full output of fdisk confirms the precise problem "Error: Can't have a partition outside the disk!" refers to, then the fix is easy: fixparts.

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Moral of the story: use Gparted for all partitioning except for resizing the Windows 7 C: partition when you need to use the inbuilt Disk Manager utility in Windows itself. As you have discovered, 3rd party Windows partitioning tools often corrupt the partition table.

---

### Post by ramidavis2 on 2014-07-25
sudo fdisk -l
Gives the same error.
I am (slowly) downloading fixparts now (56k dial up.).

---

### Post by ramidavis2 on 2014-07-25
fixparts fixed the problem!
Great program. I am on Ubuntu 11.04, so i can not speak for the current releases, but it is not in any of my repos.
Is the program availible in normal Ubuntu repos in later ubuntu editions?
This program is a true find!

---

### Post by coffeecat on 2014-07-26
Now that you have fixed your partition table, you need to re-install with a supported version of Ubuntu. 11.04 went end-of-life in October 2012, nearly two years ago. 14.04 is the current LTS (long term support) version) and is supported for 5 years from its release last April. The 14.04.1 point release ISO was made available a few days ago.

Fixparts is not in the repository, but will be available on that website for as long as the author maintains it.

---

