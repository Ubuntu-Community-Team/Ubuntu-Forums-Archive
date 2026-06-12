---
title: "Reinstalled 14.04 and now have partition mess"
date: 2014-11-08
forum: General Help
---

### Post by loren41 on 2014-11-08
After experiencing severe problems running my old Asus S96S, I decided to install a second version of the same Ubuntu in another partition and move as much data as I could to the newer version.  The new version (partition 1) now occupies 112 Gb with 1.4 Gb free and Partition 2 has 48 Gb with 39 used. 

When I look at Partition 2, I see no data.  Partition 1 contains most of what I hoped for.  Would I be smart to delete Partition 2 and expand Partition 1 to the full drive size?
Loren41

---

### Post by yancek on 2014-11-08
That would depend upon where partition one and partition two are on the disk and where the boot files are.  You should verify that you are booting from Grub from partition one before doing anything.  A simpler solution would be to just format partition two and use it as a data partition.  Posting the output of:  sudo fdisk -l as well as df -h would give some information to enable more specific advice.  Indicate which partition you are booting from, which is partition two.

---

### Post by loren41 on 2014-11-09
Yancek,

Attached is a screenshot of my disk partition setup.

loren41@asus-s96s:~$ sudo fdisk -l
[sudo] password for loren41: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ceac7

   Device Boot         Start             End         Blocks   Id  System
/dev/sda1   *           2048   219013879   109505916   83  Linux
/dev/sda2       219015166   312580095    46782465     5  Extended
/dev/sda5       308389888   312580095     2095104    82  Linux swap / Solaris
/dev/sda6       219015168   295992351    38488592   83  Linux
/dev/sda7       295993344   308383743     6195200    83  Linux

Partition table entries are not in disk order
loren41@asus-s96s:~$ sudo df -h
Filesystem      Size   Used   Avail   Use%   Mounted on
/dev/sda7       5.7G    5.4G    27M   100%    /
none              4.0K          0    4.0K      0%    /sys/fs/cgroup
udev             999M     4.0K   999M     1%    /dev
tmpfs            202M    1.2M   201M     1%    /run
none              5.0M         0    5.0M      0%   /run/lock
none           1008M      80K 1008M      1%    /run/shm
none             100M      52K  100M      1%    /run/user
/dev/sdb1        15G    1.2G     14G      8%   /media/loren41/388C-5FFD

---

