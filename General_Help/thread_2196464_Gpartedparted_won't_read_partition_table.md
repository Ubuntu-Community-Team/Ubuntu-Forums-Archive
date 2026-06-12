---
title: "Gparted/parted won't read partition table"
date: 2013-12-29
forum: General Help
---

### Post by mictho100 on 2013-12-29
Hi Guys,


I wonder if anyone might have come across this particular issue? The problem I am experiencing is very similar to this thread: [http://ubuntuforums.org/showthread.php?t=1835762](http://ubuntuforums.org/showthread.php?t=1835762)

But I am unable to use the solution offered there.

Here's some background:

I using Lubuntu 13.10 to try to read an 8GB MicroSD Card with an Android image on it and various partitions. I am trying to use GParted to shuffle some partitions around, to increase the size of the root partition. But I get an error saying "Partition 1 isn't aligned to cylinder boundaries. This is still unsupported". I have tried GParted 0.16.1, on Lubuntu, and 0.17.0 as a boot CD, directly downloaded from the GParted website.

When I run 'parted'and try to print the partition table, i get the same error "No Implementation: Partition 1 isn't aligned to cylinder boundaries.  This is still unsupported"

If I run 'sfdisk' I get the following. (the problem is with /dev/sdd)

```
sudo sfdisk -luS

Disk /dev/sda: 9729 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 152129535  152127488  83  Linux
/dev/sda2     152131582 156301311    4169730   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     152131584 156301311    4169728  82  Linux swap / Solaris

Disk /dev/sdd: 1023 cylinders, 247 heads, 62 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 10 does not have an MSDOS signature
Warning: The partition table looks like it was made
  for C/H/S=*/1/0 (instead of 1023/247/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1       3579904  15675390   12095487   b  W95 FAT32
/dev/sdd2   *     73728    106495      32768   6  FAT16
/dev/sdd3             1   3579904    3579904  85  Linux extended
/dev/sdd4             0         -          0   0  Empty
/dev/sdd5        106496    139263      32768  83  Linux
/dev/sdd6        139264    172031      32768  83  Linux
/dev/sdd7        172032   1220607    1048576  83  Linux
/dev/sdd8       1220608   2269183    1048576  83  Linux
/dev/sdd9       2269184   2301951      32768  83  Linux
/dev/sdd10      2301952   2367487      65536  83  Linux
/dev/sdd11      2367488   3022847     655360  83  Linux
/dev/sdd12      3022848   3055615      32768  83  Linux
/dev/sdd13      3055616   3579903     524288  83  Linux

```

Doing a HEX Dump with DD of the first partition shows the following (not that I understand whether there's something wrong with the info here... ;) )

```

michel@michel-Aspire-5315:~/cubietruck-android/Android_4.2_test_image_DD_dump$ sudo dd if=/dev/sdd bs=512 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000470241 s, 1.1 MB/s
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  00 00 0b 00 00 00 00 a0  36 00 ff 8f b8 00 80 00  |........6.......|
000001d0  00 00 06 00 00 00 00 20  01 00 00 80 00 00 00 00  |....... ........|
000001e0  00 00 85 00 00 00 01 00  00 00 00 a0 36 00 00 00  |............6...|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
michel@michel-Aspire-5315:~/cubietruck-android/Android_4.2_test_image_DD_dump$ sudo dd if=/dev/sdd2 bs=512 count=1 | hexdump -C
00000000  e9 00 00 20 20 20 20 20  20 20 20 00 02 04 01 00  |...        .....|
00000010  02 00 02 00 00 f8 00 01  00 00 00 00 00 00 00 00  |................|
00000020  00 00 04 00 00 01 00 00  00 00 00 56 6f 6c 75 6d  |...........Volum|
00000030  6e 00 00 00 00 00 46 41  54 31 36 20 20 20 00 00  |n.....FAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00138586 s, 369 kB/s
00000200
michel@michel-Aspire-5315:~/cubietruck-android/Android_4.2_test_image_DD_dump$ sudo dd if=/dev/sdd1 bs=512 count=1 | hexdump -C
00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 08 20 00  |.<.MSDOS5.0... .|
00000010  02 00 00 00 00 f0 00 00  00 00 00 00 00 00 00 00  |................|
00000020  ff 8f b8 00 19 2e 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 6f 00 00 00 20  20 20 20 20 20 20 20 20  |..)o...         |
00000050  20 20 46 41 54 33 32 20  20 20 00 00 00 00 00 00  |  FAT32   ......|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00182007 s, 281 kB/s
00000200


```

fdisk can also see the partition table:

```

michel@michel-Aspire-5315:~/cubietruck-android/Android_4.2_test_image_DD_dump$ sudo fdisk /dev/sdd
^[[5~[sudo] password for michel: 
Sorry, try again.
[sudo] password for michel: 
omitting empty partition (14)

Command (m for help): p

Disk /dev/sdd: 8026 MB, 8026849280 bytes
1 heads, 62 sectors/track, 252861 cylinders, total 15677440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1         3579904    15675390     6047743+   b  W95 FAT32
/dev/sdd2   *       73728      106495       16384    6  FAT16
/dev/sdd3               1     3579904     1789952   85  Linux extended
/dev/sdd5          106496      139263       16384   83  Linux
/dev/sdd6          139264      172031       16384   83  Linux
/dev/sdd7          172032     1220607      524288   83  Linux
/dev/sdd8         1220608     2269183      524288   83  Linux
/dev/sdd9         2269184     2301951       16384   83  Linux
/dev/sdd10        2301952     2367487       32768   83  Linux
/dev/sdd11        2367488     3022847      327680   83  Linux
/dev/sdd12        3022848     3055615       16384   83  Linux
/dev/sdd13        3055616     3579903      262144   83  Linux

Partition table entries are not in disk order

Command (m for help): 


```

Where can I start to find a solution for this issue? I *REALLY* need to increase the root partition on this SDcard, as I am unable to install any apps on Android. It simply runs out of space very quickly.


Many thanks,


Michel

---

### Post by oldfred on 2013-12-29
Does Android create all those little partitions?

Your flash drive does not have cylinders, drives have not actually used cylinders since hard drives went over 8GB 15 years ago. They use as BIOS setting LBA or large block allocation or preferred now AHCI. Not RAID nor IDE. Is your BIOS set for IDE or compatiblity with old drives?

But the issue is you have an extended partition and sdd2 inside the extended. Partitions are primary if one thru 4 and logical always start at 5. So sdd2 cannot be inside your extended partition, that violates partition rules.

Windows requires boot flag on a primary partition, so did sdd4 get changed somehow to be called a primary so it could have boot flag?

I would try fixparts, but do not know how you boot and then where boot flag or boot files need to be with Android.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by mictho100 on 2013-12-30
Hi Olfred,


many thanks for the quick and comprehensive reply! =)

I'm running this Android Image on a Cubietruck A20 ARM based board. It's like a Raspberry PI, but with a bit more oomph. The Android image comes in an IMG file, which is flashed to either the internal NAND or an SDCARD. And it creates all of those partitions automagically... Not sure whether any of this is intentional, or an oversight of the developer...?! 

Many thanks for clarifying the issue anyways. I will see if I can fix it myself with the information you've kindly provided. If not, I'll see if the guys at Cubietruck can suggest something.


Michel

---

