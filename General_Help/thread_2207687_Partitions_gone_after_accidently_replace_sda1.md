---
title: "Partitions gone after accidently replace sda1"
date: 2014-02-24
forum: General Help
---

### Post by rodolfo-enq on 2014-02-24
I use a dual-boot notebook with Win7 and Ubuntu 13.04. I have a 500GB HD stripped in 5 partitions: Win7, Ubuntu, Recover, Documents, Swap.  
When I was trying to clone a sd card following this instructions ([http://superuser.com/questions/460657/cloning-an-sd-card-onto-a-larger-sd-card](http://superuser.com/questions/460657/cloning-an-sd-card-onto-a-larger-sd-card)) I just accidently replace my sda1 for a sd card image. Then after I rebooted my notebook just stopped to work.  I used a bootable USB stick with Ubuntu and I saw my partitions were gone.    

My question: Please, is there any way to recover my partitions? 

More informations: 
  $ sudo fdisk -lu  
=========================================================================
Disk /dev/sda: 500.1 GB, 500107862016 bytes
60 heads, 59 sectors/track, 275924 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003a634

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         135     3854335     1927100+   6  FAT16

Disk /dev/sdb: 4025 MB, 4025810432 bytes
103 heads, 61 sectors/track, 1251 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003b574

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     7862271     3930112    b  W95 FAT32
=========================================================================     

$ sudo blkid
  =========================================================================
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="425f04b5-68ae-9e46-babc-caf79349fe79" TYPE="ext2" 
/dev/sda1: SEC_TYPE="msdos" LABEL="PHONE CARD" UUID="4488-52F3" TYPE="vfat" 
/dev/sdb1: UUID="F296-6436" TYPE="vfat"
=========================================================================

---

### Post by coldcritter64 on 2014-02-24
You may be able to recover the (back 4) partitions with testdisk, available in the repositories. Testdisk step by step guide, [[COLOR=#0000cd]--here--[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").

How big was the sd card image ? At least that much of sda1 is likely to have been overwritten data wise, and as such may not be recoverable as a workable windows system, if it was the win 7 partition you dumped the data to. You may possibly recover the back partitions, if you can work testdisk.

Note: the "data dump" utility dd also goes by another nickname ... "data destroyer", just be prepared for any losses. Depending on the size of the sd card you dumped, they could be quite substantial as dd also copies over every block bit by bit including zeroed bits. A lot of the start of the sda1 partition will likely have been blanked out as a result. Not looking too good, sorry to say.

I suspect, by the fact you can no longer see any partitions at all, you actually wrote to the full device /dev/sda and not the partition /dev/sda1; that would explain why the back partitions are no longer visible.

The partition table is part of the boot records of the drive and is on the start of the drive /dev/sda not the partition /dev/sda1; it should have been safe if you wrote to /dev/sda1 only. 

Open a terminal and use the up/down arrows to scroll back through the terminal commands history list and check for us where _*exactly*_ you wrote to please. Good luck.

---

### Post by rodolfo-enq on 2014-02-24
Thank you very much, coldcritter64!
I gonna try out testdisk tomorrow morning and I'll report here. I'm pretty sure my sda1 partition was my windows recover partition.

sd card image is 2GB.

---

### Post by Mark Phelps on 2014-02-25
It's generally a bad idea to use Linux filesystem utilities on Windows filesystems.  While they often work OK, they do sometimes fail -- and when they do, they can leave the Windows filesystem in a corrupted state. 

You should download and burn the Minitool Partition Wizard Boot CD (from a Windows PC). That is a free Windows partitioning utility that understands NTFS partitions. It can do all the Windows filesystem partitioning that you need. It may be able to recover all the partitions for you.

---

### Post by rodolfo-enq on 2014-02-25
Apparently I lost my win7 partition. TestDisk returned this:

==============================================================
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
>  FAT16 >32M               0   2 10   239 234 34    3854176
   HPFS - NTFS          17044 123 40 19457  21 20   38758400 [SAMSUNG_REC]
   HPFS - NTFS          19457  53 53 53385  76  3  545054720 [Documentos]
   Linux                53385  76  4 60737  16 15  118106112
   Linux Swap           60737 211 19 60801  80 15    1019904

Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, blocksize=32768, 1973 MB / 1881 MiB
==============================================================

---

### Post by rodolfo-enq on 2014-02-26
[IMG]http://www.yoimg.com/di-9LH7.png[/IMG]

That happened I lost my windows partition but this is not a big deal. I use Ubuntu most of time.

---

