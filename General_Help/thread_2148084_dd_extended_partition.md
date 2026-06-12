---
title: "dd extended partition"
date: 2013-05-23
forum: General Help
---

### Post by amanisdude on 2013-05-23
[FONT=arial]Hi everyone!

I am having somewhat of an odd time trying to backup an extended partition using [FONT=courier new]dd[/FONT].

The extended partition is located on [FONT=courier new]/dev/sda3[/FONT] and is roughly 253 GiB in size. It holds logical partitions [FONT=courier new]/dev/sda5[/FONT], [FONT=courier new]/dev/sda6[/FONT], and [FONT=courier new]/dev/sda7[/FONT].

The problem happens when I try to use this command: ```
dd if=/dev/sda3 of=/media/backup/extended-partition.img bs=1M
```

In theory, I would think this would back up all 253 GiB and all logical partitions thereunder (since the volumes are nested).

However, this is the result I get:```
0+1 records in
0+1 records out
1024 bytes (1.0 kB) copied, 0.000343302 s, 3.0 MB/s
```

What am I doing wrong here?? I would imagine that, since an extended partition is actually a kind of primary partition, it would backup the whole thing, not just the first megabyte. Any help in understanding this would be much appreciated. :D
[/FONT]___________________

[FONT=arial]Here's some more disk information for [FONT=courier new]/dev/sda[/FONT]:

**[FONT=courier new]fdisk[/FONT]**:```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71ed71ed


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    26626047    13312000   27  Hidden NTFS WinRE
/dev/sda2   *    26626048    26830847      102400    7  HPFS/NTFS/exFAT
/dev/sda3        26830848   557340671   265254912    5  Extended
/dev/sda4       557340672   767055871   104857600    7  HPFS/NTFS/exFAT
/dev/sda5        26832896   236548095   104857600    7  HPFS/NTFS/exFAT
/dev/sda6       347625472   557340671   104857600    7  HPFS/NTFS/exFAT
/dev/sda7       236550144   272889855    18169856   83  Linux



Partition table entries are not in disk order
```**[FONT=courier new]sfdisk[/FONT]**:```
Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0


   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   1657-   1658-  13312000   27  Hidden NTFS WinRE
/dev/sda2   *   1657+   1670-     13-    102400    7  HPFS/NTFS/exFAT
/dev/sda3       1670+  34692-  33023- 265254912    5  Extended
/dev/sda4      34692+  47747-  13055- 104857600    7  HPFS/NTFS/exFAT
/dev/sda5       1670+  14724-  13055- 104857600    7  HPFS/NTFS/exFAT
/dev/sda6      21638+  34692-  13055- 104857600    7  HPFS/NTFS/exFAT
/dev/sda7      14724+  16986-   2263-  18169856   83  Linux
```[/FONT][FONT=arial]&#8203;-[/FONT]***amanisdude***[FONT=arial]
[/FONT]___________________

**EDIT**: It might be worth noting that the version of [FONT=courier new]dd[FONT=arial] I am using is [FONT=courier new]8.13[FONT=arial] in case that bears any relevance.
[/FONT][/FONT][/FONT][/FONT]___________________

---

### Post by ohnonot on 2013-05-24
i think the extended partition /dev/sda3 only holds information on the extended partitions and nothing else, so dd basically did the right thing. i guess you have to backup the logical partitions 1 by 1, and not sda3 itself since it's only some kind of meta partition.

---

### Post by Bucky Ball on 2013-05-24
> **ohnonot said:**
> I guess you have to backup the logical partitions 1 by 1, and not sda3 itself since it's only some kind of meta partition.

Exactly. The extended partition is nothing more than a bucket, a holder, a container, for the partitions inside it. It is nothing! You are attempting to backup the bucket and not what's in it. Do the partitions inside the extended partition, not the extended partition.

---

