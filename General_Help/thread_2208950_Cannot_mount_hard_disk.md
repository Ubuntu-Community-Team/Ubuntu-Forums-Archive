---
title: "Cannot mount hard disk"
date: 2014-03-03
forum: General Help
---

### Post by xeonix on 2014-03-03
I am having a hard disk, I have a very important data on it. I could not mount the disk.


Here are the images:

[IMG]http://i57.tinypic.com/jutjcy.jpg[/IMG]

[IMG]http://i58.tinypic.com/1zxqzoo.png[/IMG]


```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00034daf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   400001023   199999488   83  Linux
/dev/sda2      1233598462  1250263039     8332289    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda3       400003072  1233598461   416797695   83  Linux
/dev/sda5      1233598464  1250263039     8332288   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001cf00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           48195     8273474     4112640   fd  Linux RAID autodetect
/dev/sdb2         8273475  1953520064   972623295   fd  Linux RAID autodetect
/dev/sdb3               1       48194       24097   da  Non-FS data

Partition table entries are not in disk order


```

dmesg |tail
```

[ 9218.154133] EXT3-fs (sdb1): recovery required on readonly filesystem
[ 9218.154143] EXT3-fs (sdb1): error: write access unavailable, cannot proceed
[ 9249.322212] XFS (sdb2): Mounting Filesystem
[ 9249.473679] XFS (sdb2): recovery required on read-only device.
[ 9249.473683] XFS (sdb2): write access unavailable, cannot proceed.
[ 9249.473685] XFS (sdb2): log mount/recovery failed: error 30
[ 9249.473721] XFS (sdb2): log mount failed


```

---

### Post by ajgreeny on 2014-03-03
```
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           48195     8273474     4112640   fd  [COLOR=#ff0000]Linux RAID autodetect[/COLOR]
/dev/sdb2         8273475  1953520064   972623295   fd  [COLOR=#ff0000]Linux RAID autodetect[/COLOR]
/dev/sdb3               1       48194       24097   da  Non-FS data
```
I imagine this is a result of the partitions being used in some way in a raid setup.
Unfortunately I do not know anything about dealing with raid, but this may give you more chance of searching in a meaningful way.

---

### Post by xeonix on 2014-03-03
@ajgreeny:
Thanks.

As it was actually NAS drive, which I took out of network, and removed the case and took out the hard disk and was trying to mount.
However, as it contained very important data, I used write blocker (TABLEAU).
As, the errors indicated, I risked and attached it to my Desktop as internal Hard disk and it mounted on a fly.

I was just gessuing, wether there would have any other methods, which could have helped me mount the disk in *read only* mode.

---

