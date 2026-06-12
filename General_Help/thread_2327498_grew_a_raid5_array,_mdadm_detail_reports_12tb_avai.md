---
title: "grew a raid5 array, mdadm detail reports 12tb available, /dev/md shows only 8tb"
date: 2016-06-11
forum: General Help
---

### Post by jason63 on 2016-06-11
Original Array Raid5;

/dev/md127
3x 4TB WD RED Drives

each with 1 LINUX EXT Partition

sdb1
sdc1
sdd1

```
root@ubuntu-server:/mnt/REDraid5# df -H
Filesystem      Size  Used Avail Use% Mounted on
udev            6.3G  8.2k  6.3G   1% /dev
tmpfs           1.3G  4.3M  1.3G   1% /run
/dev/dm-0        93G   61G   28G  69% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
none            5.3M  4.1k  5.3M   1% /run/lock
none            6.3G  4.1k  6.3G   1% /run/shm
none            105M     0  105M   0% /run/user
/dev/sde1       5.4G  397M  4.7G   8% /boot
/dev/sdf1       493G  220G  248G  48% /mnt/IP_CAMERAS
/dev/md0        4.0T  3.7T  105G  98% /mnt/GREENraid5
/dev/md127      8.0T  7.8T  180G  98% /mnt/REDraid5
root@ubuntu-server:/mnt/REDraid5#



```

grew the array to include /dev/sda1

```
root@ubuntu-server:/mnt/REDraid5# mdadm --detail /dev/md127/dev/md127:
        Version : 1.2
  Creation Time : Sun Dec 28 20:54:09 2014
     Raid Level : raid5
     Array Size : 11720655360 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 3906885120 (3725.90 GiB 4000.65 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Sat Jun 11 09:51:27 2016
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : ubuntu-server:1  (local to host ubuntu-server)
           UUID : 51f06d57:3e178738:b40b67d1:03810b63
         Events : 10059


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
       2       8       33        2      active sync   /dev/sdc1
       4       8        1        3      active sync   /dev/sda1
root@ubuntu-server:/mnt/REDraid5#



```


Webmin, mdadm --detail reports 11TB of usable space, but the mounted drive still shows 8TB

```
root@ubuntu-server:/mnt/REDraid5# df -H
Filesystem      Size  Used Avail Use% Mounted on
udev            6.3G  8.2k  6.3G   1% /dev
tmpfs           1.3G  4.3M  1.3G   1% /run
/dev/dm-0        93G   61G   28G  69% /
none            4.1k     0  4.1k   0% /sys/fs/cgroup
none            5.3M  4.1k  5.3M   1% /run/lock
none            6.3G  4.1k  6.3G   1% /run/shm
none            105M     0  105M   0% /run/user
/dev/sde1       5.4G  397M  4.7G   8% /boot
/dev/sdf1       493G  220G  248G  48% /mnt/IP_CAMERAS
/dev/md0        4.0T  3.7T  105G  98% /mnt/GREENraid5
/dev/md127      8.0T  7.8T  180G  98% /mnt/REDraid5
root@ubuntu-server:/mnt/REDraid5#



```

```
root@ubuntu-server:/mnt# fdisk -l /dev/md127

Disk /dev/md127: 12002.0 GB, 12001951088640 bytes
2 heads, 4 sectors/track, -1364803456 cylinders, total 23441310720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/md127 doesn't contain a valid partition table
root@ubuntu-server:/mnt#
```




What am I missing? The array is still active and working fine, just maxed out at 98% usage which is why i grew the array in the first place.

Thanks guys!

---

