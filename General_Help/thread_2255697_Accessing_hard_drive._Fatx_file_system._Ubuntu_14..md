---
title: "Accessing hard drive. Fatx file system. Ubuntu 14.04"
date: 2014-12-06
forum: General Help
---

### Post by Redacted on 2014-12-06
I have a hard drive that is using Fatx file system and I'm trying to mount it and I just can't seem to get it running.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d03f5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   972949503   486473728   83  Linux
/dev/sda2       972951550   976771071     1909761    5  Extended
/dev/sda5       972951552   976771071     1909760   82  Linux swap / Solaris


Disk /dev/sdb: 20.0 GB, 20003880960 bytes
64 heads, 32 sectors/track, 19077 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table



```

I just created a virtual machine and mounted it there. if someone else has problem, I can give a more detailed explanation.

---

