---
title: "Partitions problem"
date: 2007-04-29
forum: General Help
---

### Post by Dod_basim on 2007-04-29
Hello
I just reinstalled my ubuntu (changed from 64bit to 32bit) and i wanted to keep my Thinkpad fat32 restore partition (about 5Gb) and use all the rest as a single boot machine (ubuntu 7.04).
I had some problem and the only thing was possible was to devide the disk into more than 2 partitions.

now i have a total mess with 50 Gb missing.

> fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6805    54661131    b  W95 FAT32
/dev/sda2            9181        9728     4399920   12  Compaq diagnostics Partition 2 does not end on cylinder boundary.
/dev/sda3   *        6806        8914    16940542+  83  Linux
/dev/sda4            8915        9180     2136645    5  Extended
/dev/sda5            9013        9180     1349428+  82  Linux swap / Solaris
/dev/sda6            8915        9012      787122   82  Linux swap / Solaris

Partition table entries are not in disk order



what can i do?
I know ubuntu need one swap partition and a root (the only i need is this Thinkpad  fat32 partition)


thanks alot

---

