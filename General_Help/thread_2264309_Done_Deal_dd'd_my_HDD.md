---
title: "Done Deal: dd'd my HDD"
date: 2015-02-06
forum: General Help
---

### Post by Mk32 on 2015-02-06
I figured it would happen eventually, and today I did so. 

Went to write a disk image (~80MB image) to a micro-SD card, but I put in by mistake, /dev/sda instead of /dev/sdb. 

It copied about 22MB before I recognized it and did an emergency power-off. Probably should have control-C'd it. 

System: Compaq E500, P3 900MHz, 60GB had drive, five operating systems as such: 

Primary: FAT32 Windows 98SE
Extended: Windows 2000 Server, Windows 2000 SP4, Windows XP, Ubuntu 9.10, and last ~512MB is swap space. 

I've read [this article](https://help.ubuntu.com/community/Grub2/Installing) on restoring GRUB, but...it won't work. I have Hiren's Ultimate Boot CD on hand, probably 2 year old version. I ran TestDisk 6.14 but it couldn't find any logical partitions. 

Clues?

---

### Post by Mk32 on 2015-02-06
I show the following partitions in TestDisk:

```

Partition                   Start               End             Size in sectors
* FAT32               0    0    33       8    40    32       131040 [NookManager]
L Linux Swap       6270    1     1     6331   254   63       995967
L Linux            6332    1     1     7295   254   63     15486597

```

Is that meaning that I can rebuild the partition table with Linux accounted for, but the Windows partitions are a goner? I fully expect to have to rebuild Windows 98SE.

---

### Post by sudodus on 2015-02-06
Those first 22 MB are overwritten and lost. File data that w stored behind that part of the drive are there, but you should not mount anything or create anything on the drive if the data are important. Instead I suggest that you make a cloned copy and do the rescue work on that drive. Trying with ***Testdisk*** is worthwhile, but if it fails you can resort to ***PhotoRec***, which might help you recover several important files even without a file system. It is a lot of hard work, but is possible.

-o-

***dd*** is risky. If you want to clone your drive, ***Clonezilla*** is a better tool. If you want to create a USB boot drive with the dd method, ***mkusb*** is there to make it safer.

---

### Post by Mk32 on 2015-02-06
I can't detect the Windows partitions. The Linux and swap partitions, as shown earlier, are. 

There is some data in the Linux system I could really use, mainly some backup images and some stuff in the Sticky Notes program which I thought I taught myself not to use. How do I boot into the Linux system? Perhaps I could try doing a chroot operation?

EDIT: I've seen and heard about ways of manually detecting partition LBAs and using those to manually construct a partition table based on the sector start and stop blocks. This laptop never really had anything critical on it, until now of course, but it'd be nice to dodge the two days it takes to install and update all five operating systems...

---

### Post by sudodus on 2015-02-07
I have not succeeded to recover file systems with Testdisk, but I have read threads at the Ubuntu Forums with such success stories. I have recovered files with PhotoRec.

I suggest that you search for and recover at least the most important files. If it works with Testdisk, great, the process will be fairly fast, otherwise it will be slow with PhotoRec.

If you can restore some of the linux file systems, you need not boot into them, you can boot from a DVD/USB boot drive, mount the restored file system and save the files. It might work to re-install grub according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

It is usually faster and easier to re-install than to repair operating systems or file systems. [COLOR=#696969]The best option would be to restore from a backup (if you have a backup).[/COLOR]

---

### Post by Mk32 on 2015-02-08
I ended up using TestDisk to make the Linux partition a primary bootable one, then used a Live CD to rebuild GRUB. 

This  laptop is mostly used for odd stuff, so aside from some Nook Android  backup images, there wasn't much on it that was valuable, if anything.  Some save game files though, but I am not aware of any recovery programs  that can do deep scanning of disks to recover files and only recover  the ones I want that will run in Linux. Maybe on a Knoppix DVD though,  which this thing is too old to run a newer version of Knoppix (and only  has 384MB RAM, as 512 causes issues).

---

### Post by sudodus on 2015-02-08
Congratulations :KS

PhotoRec scans the drive for patterns that define the beginning (and end) of various file types. I think it started as a tool to recover photos from flash cards, and has developed into a tool that can recognize many file types. Normally the file content will be saved, but not the file name and directory path (except if the file name is saved inside the file content).

[http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec)

If you don't want to drown in a lot of files, you can limit the recovery to one or a few file types.

It might or might not recognize the file type of those saved game files.

---

