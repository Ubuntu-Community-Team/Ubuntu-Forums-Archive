---
title: "Corrupt GPT table on Ubuntu 16.04"
date: 2018-01-30
forum: General Help
---

### Post by luca12354 on 2018-01-30
Good evening to everyone,
I write because I have a problem with my laptop (Samsung NP350V35C, Intel core i7 ), on which I managed to install successfully Ubuntu 16.04 and WIndows 10 in dual boot. For half a year things worked fine, but this morning Windows did not want to boot, and crashed on a black screen. Ubuntu worked fine, so after some research online, I found out that maybe there was a problem with Windows bootloader, and so I installed and run Boot-Repair, which gave the error "cannot read dev/sda"(I followed this for the installation: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).

However, Boot-repair also erased all my grub settings and now I can only boot Ubuntu live from my USB pendrive. I tried to install Boot-repair again in the hope of fixing the bootloader, but when I launch:

sudo apt-get install -y boot-repair

I get this:
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'update-inetd': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


Again, looking online I understood that most of the times Input/output errors are due to a damaged disk, and so I run fdisk, which gives me the following:

=======================================================================

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.4 GiB, 1532116992 bytes, 2992416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C58C71B5-7216-4978-9C0A-10A9E160C883

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1023999    1021952   499M Windows recovery environment
/dev/sda2     1024000    1638399     614400   300M EFI System
/dev/sda3     1638400    1900543     262144   128M Microsoft reserved
/dev/sda4     1900544 1686257223 1684356680 803.2G Microsoft basic data
/dev/sda5  1686257664 1688354815    2097152     1G Linux swap
/dev/sda6  1688354816 1895972003  207617188    99G Linux filesystem
/dev/sda7  1895972864 1897756671    1783808   871M Windows recovery environment
/dev/sda8  1897756672 1951426559   53669888  25.6G Windows recovery environment
/dev/sda9  1951426560 1953523711    2097152     1G Windows recovery environment




Disk /dev/sdb: 3.8 MiB, 4006400 bytes, 7825 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x73696420

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1       1919950958 2464388050  544437093 259.6G 20 unknown
/dev/sdb2       1330184202 1869160489  538976288   257G 6b unknown
/dev/sdb3        538989391 1937352302 1398362912 666.8G 53 OnTrack DM6 Aux3
/dev/sdb4  *    1394627663 1394648999      21337  10.4M 49 unknown

Partition table entries are not in disk order.


Disk /dev/sdc: 3.7 GiB, 4002602496 bytes, 7817583 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0d66cd15

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdc1  *          0 3100799 3100800  1.5G  0 Empty
/dev/sdc2       3006684 3011355    4672  2.3M ef EFI (FAT-12/16/32)

================================================================================

Then, I run gdisk to try and fix the problem, and here is what I get:

_____________________________________________________

sudo gdisk /dev/sda
GPT fdisk (gdisk) version 1.0.1

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! Error 5 reading partition table for CRC check!
Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y
OK; writing new GUID partition table (GPT) to /dev/sda.
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.


__________________________________

I tried the 'e' option, but it does not solve the problem.
Sorry for the lengthy post, and thanks in advance to anyone who tries to help me.

---

### Post by oldfred on 2018-01-31
You have gone thru about all the repair options I know or suggest.

 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table) 

Not sure if rodsbooks site has further suggestions?

Have you also checked drive with Disks, and icon in upper right corner that has Smart Status? While it can run lots of tests, all I really know is whether it says drive is good or bad.

The author of gdisk, Rod Smith sometimes posts in AskUbuntu. If nothing else you can try there also.
If you have gdisk & error in title he may then see your post.

---

