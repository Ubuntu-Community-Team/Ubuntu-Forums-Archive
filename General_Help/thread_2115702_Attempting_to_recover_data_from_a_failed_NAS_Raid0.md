---
title: "Attempting to recover data from a failed NAS Raid0 Configuration"
date: 2013-02-13
forum: General Help
---

### Post by trinsic1 on 2013-02-13
System Information
Manufacturer: Macally 
Model: NSA2-S350NAS
Product Name           GBNAS2
Firmware Version           2.6.3-n


I  Initialized this device with two 250gig sata hard drives using the ext3  file system. It ran for a couple of months. all of a sudden it became  inaccessible. I rebooted it and the data from my shared folders were  completely gone. When I went into the nas utilities the logs show some disk errors and the drive information shows the disk with a clean partition as if it was formatted...

So I put the to disks on my linux box to see what happened and here is the results:

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x55b6e031

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      112454       56227   fd  Linux raid autodetect
/dev/sda2          112455   487877984   243882765   fd  Linux raid autodetect
/dev/sda3       487877985   488392064      257040   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b649230

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      112454       56227   fd  Linux raid autodetect
/dev/sdb2          112455   487877984   243882765   fd  Linux raid autodetect
/dev/sdb3       487877985   488392064      257040   82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
224 heads, 19 sectors/track, 73444 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c54b3

Partition table entries are not in disk order

Disk /dev/md1: 499.5 GB, 499471745024 bytes
2 heads, 4 sectors/track, 121941344 cylinders, total 975530752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x451757ab

    Device Boot      Start         End      Blocks   Id  System

Disk /dev/md0: 114 MB, 114950144 bytes
2 heads, 4 sectors/track, 28064 cylinders, total 224512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


``````
ARRAY /dev/md0 UUID=7eee0102:dcd80ca2:3b134edd:d71f862d
ARRAY /dev/md1 UUID=246baad2:73495195:ac5bb834:861758fd
``````


Tue Feb 12 18:30:10 2013
Command line: TestDisk

TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 3.5.0-17-generic (#28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012) i686
Compiler: GCC 4.7
Compilation date: 2012-10-01T12:56:22
ext2fs lib: 1.42.5, ntfs lib: libntfs-3g, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       488397168 sectors
/dev/sda: user_max   488397168 sectors
/dev/sda: native_max 488397168 sectors
/dev/sda: dco        488397168 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       488397168 sectors
/dev/sdb: user_max   488397168 sectors
/dev/sdb: native_max 488397168 sectors
/dev/sdb: dco        488397168 sectors
/dev/sdc: LBA, HPA, LBA48, DCO support
/dev/sdc: size       312581808 sectors
/dev/sdc: user_max   312581808 sectors
/dev/sdc: native_max 312581808 sectors
/dev/sdc: dco        312581808 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - Hitachi HTS543225L9A300, S/N:081104FB2F00LLJDYS4A, FW:FBEOC40C
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - WDC WD2500BEVS-75UST0, S/N:WD-WXE708J1H977, FW:01.01A01
Disk /dev/sdc - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512 - WDC WD1600AAJB-00PVA0, S/N:WD-WMAP93705027, FW:00.07H00
Disk /dev/md0 - 114 MB / 109 MiB - CHS 28064 2 4, sector size=512
Disk /dev/md1 - 499 GB / 465 GiB - CHS 121941344 2 4, sector size=512

Partition table type (auto): None
Disk /dev/md1 - 499 GB / 465 GiB
Partition table type: Intel
Partition table type (auto): None
Disk /dev/md0 - 114 MB / 109 MiB
Partition table type: Intel

Analyse Disk /dev/md0 - 114 MB / 109 MiB - CHS 28064 2 4
Current partition structure:

Partition sector doesn't have the endmark 0xAA55
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/md0 - 114 MB / 109 MiB - CHS 28064 2 4

Results

interface_write()
 
No partition found or selected for recovery

search_part()
Disk /dev/md0 - 114 MB / 109 MiB - CHS 28064 2 4

Results

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
Store new MBR code
write_all_log_i386: starting...
No extended partition
Partition table type (auto): None
Disk /dev/md1 - 499 GB / 465 GiB
Partition table type: Intel

Analyse Disk /dev/md1 - 499 GB / 465 GiB - CHS 121941344 2 4
Current partition structure:
No partition is bootable
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/md1 - 499 GB / 465 GiB - CHS 121941344 2 4
Search for partition aborted

Results

interface_write()
 
No partition found or selected for recovery
simulate write!

write_mbr_i386: starting...
write_all_log_i386: starting...
No extended partition

Analyse Disk /dev/md1 - 499 GB / 465 GiB - CHS 121941344 2 4
Current partition structure:
No partition is bootable
Ask the user for vista mode
Allow partial last cylinder : No
search_vista_part: 0

search_part()
Disk /dev/md1 - 499 GB / 465 GiB - CHS 121941344 2 4
BAD_RS LBA=2896947548 2216
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 0E
     FAT16 LBA            362118443   1  1 898909792   1  4 4294330796
This partition ends after the disk limits. (start=2896947548, size=4294330796, end=2896311047, disk end=975530752)
BAD_RS LBA=3997825006 2440
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 01
     FAT12                499728125   1  3 996590799   1  2 3974901392
This partition ends after the disk limits. (start=3997825006, size=3974901392, end=3677759101, disk end=975530752)
BAD_RS LBA=792333299 2157
check_part_i386 failed for partition type 04
     FAT16 <32M           99041662   0  4 185263570   1  2  689775267
This partition ends after the disk limits. (start=792333299, size=689775267, end=1482108565, disk end=975530752)
BAD_RS LBA=2426923863 1175
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           303365482   1  4 717534810   1  4 3313354625
This partition ends after the disk limits. (start=2426923863, size=3313354625, end=1445311191, disk end=975530752)
BAD_RS LBA=729665802 4271
check_part_i386 failed for partition type 0E
     FAT16 LBA            91208225   0  3 540484708   1  3 3594211869
This partition ends after the disk limits. (start=729665802, size=3594211869, end=28910374, disk end=975530752)
BAD_RS LBA=2735604190 501
check_part_i386 failed for partition type 07
     HPFS - NTFS          341950523   1  3 542284390   1  3 1602670937
This partition ends after the disk limits. (start=2735604190, size=1602670937, end=43307830, disk end=975530752)
BAD_RS LBA=483230392 6757
check_part_i386 failed for partition type 06
     FAT16 >32M           60403799   0  1 300251231   0  1 1918779457
This partition ends after the disk limits. (start=483230392, size=1918779457, end=2402009848, disk end=975530752)
BAD_RS LBA=3511007406 5603
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 0C
     FAT32 LBA            438875925   1  3 470920195   1  4  256354162
This partition ends after the disk limits. (start=3511007406, size=256354162, end=3767361567, disk end=975530752)
BAD_RS LBA=3463867813 3556
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 06
     FAT16 >32M           432983476   1  2 783753233   0  4 2806158055
This partition ends after the disk limits. (start=3463867813, size=2806158055, end=1975058571, disk end=975530752)
BAD_RS LBA=1439504035 6354
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 06
     FAT16 >32M           179938004   0  4 341721990   0  2 1294271887
This partition ends after the disk limits. (start=1439504035, size=1294271887, end=2733775921, disk end=975530752)
BAD_RS LBA=939791292 6812
check_part_i386 failed for partition type 04
     FAT16 <32M           117473911   1  1 216082748   0  2  788870694
This partition ends after the disk limits. (start=939791292, size=788870694, end=1728661985, disk end=975530752)
BAD_RS LBA=1674230623 1522
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           209278827   1  4 567909936   0  2 2869048867
This partition ends after the disk limits. (start=1674230623, size=2869048867, end=248312193, disk end=975530752)
BAD_RS LBA=551144879 2363
check_part_i386 failed for partition type 04
     FAT16 <32M           68893109   1  4 350700733   1  3 2254460992
This partition ends after the disk limits. (start=551144879, size=2254460992, end=2805605870, disk end=975530752)
BAD_RS LBA=841654641 8250
check_part_i386 failed for partition type 07
     HPFS - NTFS          105206830   0  2 106522589   0  4   10526075
BAD_RS LBA=4244798450 7793
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           530599806   0  3 888687447   0  3 2864701129
This partition ends after the disk limits. (start=4244798450, size=2864701129, end=2814532282, disk end=975530752)
BAD_RS LBA=3696111849 1405
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 06
     FAT16 >32M           462013981   0  2 798479133   1  2 2691721221
This partition ends after the disk limits. (start=3696111849, size=2691721221, end=2092865773, disk end=975530752)
BAD_RS LBA=253870063 4625
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 06
     FAT16 >32M           568604669   1  4 947353014   1  1 3029986758
This partition ends after the disk limits. (start=253870063, size=3029986758, end=3283856820, disk end=975530752)
BAD_RS LBA=3661194016 605
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           457649252   0  1 485400409   0  1  222009257
This partition ends after the disk limits. (start=3661194016, size=222009257, end=3883203272, disk end=975530752)
BAD_RS LBA=3382166175 391
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 0E
     FAT16 LBA            422770771   1  4 693729736   0  2 2167671715
This partition ends after the disk limits. (start=3382166175, size=2167671715, end=1254870593, disk end=975530752)
BAD_RS LBA=3705755996 2557
check_part_i386 failed for partition type 07
     HPFS - NTFS          463219499   1  1 616717898   0  4 1227987192
This partition ends after the disk limits. (start=3705755996, size=1227987192, end=638775891, disk end=975530752)
BAD_RS LBA=3735261656 1510
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 01
     FAT12                466907707   0  1 975730819   0  2 4070584898
This partition ends after the disk limits. (start=3735261656, size=4070584898, end=3510879257, disk end=975530752)
BAD_RS LBA=2022054054 2611
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 0E
     FAT16 LBA            252756756   1  3 710039106   1  2 3658258800
This partition ends after the disk limits. (start=2022054054, size=3658258800, end=1385345557, disk end=975530752)
BAD_RS LBA=61743046 7345
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           544588792   1  3 963408553   1  4 3350558090
This partition ends after the disk limits. (start=61743046, size=3350558090, end=3412301135, disk end=975530752)
BAD_RS LBA=2008403795 5643
check_part_i386 failed for partition type 07
     HPFS - NTFS          251050474   0  4 632328483   1  1 3050224074
This partition ends after the disk limits. (start=2008403795, size=3050224074, end=763660572, disk end=975530752)
BAD_RS LBA=1452024892 1693
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 01
     FAT12                181503111   1  1 670477295   0  1 3911793469
This partition ends after the disk limits. (start=1452024892, size=3911793469, end=1068851064, disk end=975530752)
BAD_RS LBA=3614067075 38
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           451758384   0  4 873368163   1  2 3372878235
This partition ends after the disk limits. (start=3614067075, size=3372878235, end=2691978013, disk end=975530752)
BAD_RS LBA=3209306353 1782
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           401163294   0  2 736823313   1  1 2685280156
This partition ends after the disk limits. (start=3209306353, size=2685280156, end=1599619212, disk end=975530752)
BAD_RS LBA=2580029829 400
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 0B
     FAT32                322503728   1  2 672343860   1  1 2798721056
This partition ends after the disk limits. (start=2580029829, size=2798721056, end=1083783588, disk end=975530752)
BAD_RS LBA=1225010437 905
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 0C
     FAT32 LBA            153126304   1  2 232277364   0  1  633208476
This partition ends after the disk limits. (start=1225010437, size=633208476, end=1858218912, disk end=975530752)
BAD_RS LBA=2279927864 4369
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           284990983   0  1 470483955   0  2 1483943778
This partition ends after the disk limits. (start=2279927864, size=1483943778, end=3763871641, disk end=975530752)
BAD_RS LBA=3407117253 5687
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 0C
     FAT32 LBA            425889656   1  2 643736563   0  3 1742775254
This partition ends after the disk limits. (start=3407117253, size=1742775254, end=854925210, disk end=975530752)
BAD_RS LBA=2905575899 4795
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 0C
     FAT32 LBA            363196987   0  4 810575049   1  1 3579024498
This partition ends after the disk limits. (start=2905575899, size=3579024498, end=2189633100, disk end=975530752)
BAD_RS LBA=2359170585 4146
check_part_i386 failed for partition type 07
     HPFS - NTFS          294896323   0  2 454125460   1  3 1273833102
This partition ends after the disk limits. (start=2359170585, size=1273833102, end=3633003686, disk end=975530752)
BAD_RS LBA=3188953853 1983
check_FAT: can't read FAT boot sector
check_part_i386 failed for partition type 04
     FAT16 <32M           398619231   1  2 854758652   0  2 3649115365
This partition ends after the disk limits. (start=3188953853, size=3649115365, end=2543101921, disk end=975530752)
Disk /dev/md1 - 499 GB / 465 GiB - CHS 121941344 2 4
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (499 GB / 465 GiB) seems too small! (< 4082 GB / 3801 GiB)
The following partitions can't be recovered:
     FAT16 >32M           60403799   0  1 300251231   0  1 1918779457
     FAT16 <32M           68893109   1  4 350700733   1  3 2254460992
     FAT16 LBA            91208225   0  3 540484708   1  3 3594211869
     FAT16 <32M           99041662   0  4 185263570   1  2  689775267
     FAT16 <32M           117473911   1  1 216082748   0  2  788870694
     FAT32 LBA            153126304   1  2 232277364   0  1  633208476
     FAT16 >32M           179938004   0  4 341721990   0  2 1294271887
     FAT12                181503111   1  1 670477295   0  1 3911793469
     FAT16 <32M           209278827   1  4 567909936   0  2 2869048867
     HPFS - NTFS          251050474   0  4 632328483   1  1 3050224074
     FAT16 LBA            252756756   1  3 710039106   1  2 3658258800
     FAT16 <32M           284990983   0  1 470483955   0  2 1483943778
     HPFS - NTFS          294896323   0  2 454125460   1  3 1273833102
     FAT16 <32M           303365482   1  4 717534810   1  4 3313354625
     FAT32                322503728   1  2 672343860   1  1 2798721056
     HPFS - NTFS          341950523   1  3 542284390   1  3 1602670937
     FAT16 LBA            362118443   1  1 898909792   1  4 4294330796
     FAT32 LBA            363196987   0  4 810575049   1  1 3579024498
     FAT16 <32M           398619231   1  2 854758652   0  2 3649115365
     FAT16 <32M           401163294   0  2 736823313   1  1 2685280156
     FAT16 LBA            422770771   1  4 693729736   0  2 2167671715
     FAT32 LBA            425889656   1  2 643736563   0  3 1742775254
     FAT16 >32M           432983476   1  2 783753233   0  4 2806158055
     FAT32 LBA            438875925   1  3 470920195   1  4  256354162
     FAT16 <32M           451758384   0  4 873368163   1  2 3372878235
     FAT16 <32M           457649252   0  1 485400409   0  1  222009257
     FAT16 >32M           462013981   0  2 798479133   1  2 2691721221
     HPFS - NTFS          463219499   1  1 616717898   0  4 1227987192
     FAT12                466907707   0  1 975730819   0  2 4070584898
     FAT12                499728125   1  3 996590799   1  2 3974901392
     FAT16 <32M           530599806   0  3 888687447   0  3 2864701129
     FAT16 <32M           544588792   1  3 963408553   1  4 3350558090
     FAT16 >32M           568604669   1  4 947353014   1  1 3029986758
Warning: the current number of heads per cylinder is 2 but the correct value may be 255.

TestDisk exited normally.

```The first raid array is the nas system partition and the second array is my shared drive. I tried check out the partition information on the first nas system array and got an bad sector error when scanning the disk for lost partitions using testdisk.

When I scanned the second array for lost partitions it listed all this partitions accept for my ext3 partition That I had though i used to format the disk from the nas utilities when I first initialized the device.

I tried to use photorec to recover the files, but its recovering all the files with no file names (I.E randomly generated file names).

Im wondering if anyone that is more knowledgeable than me regarding data recovery can point me in the right direction is if there is away to either recover the lost partition information so I can recover the file with the proper names.

Any help would be appreciated.

---

### Post by dcstar on 2013-02-14
> **trinsic1 said:**
> 
..........
Any help would be appreciated.

"RAID 0" is the exact opposite of RAID - you lose one device and you lose ALL of your data.

---

### Post by trinsic1 on 2013-02-14
> **dcstar said:**
> "RAID 0" is the exact opposite of RAID - you lose one device and you lose ALL of your data.
I understand that. both drives are functioning enough to perform data recovery.
What im asking is if there is another way to recover the partition information or if I missed something in the recovery process.

---

