---
title: "Disk Space runs full: du vs df"
date: 2015-07-09
forum: General Help
---

### Post by manfred87 on 2015-07-09
Hallo,

i have the following problem: my disksize is 412 GB, i have 192 GB files, but disk is 92% full. so what could fill the other space? how can i clean this up and use the other space?
side effect: /boot runs full, but this can be resolved when deleting kernels..

```
df -mFilesystem               1M-blocks   Used Available Use% Mounted on
/dev/mapper/lvm+ssd-root    412631 357141     34508  92% /
none                             1      0         1   0% /sys/fs/cgroup
udev                         16053      1     16053   1% /dev
tmpfs                         3214      2      3213   1% /run
none                             5      0         5   0% /run/lock
none                         16069     69     16000   1% /run/shm
none                           100      1       100   1% /run/user
/dev/md0p1                     226    207         4  99% /boot
```

```
 du -smc /* | sort -n -r
192722  total
181381  /home
7383    /usr
1527    /lib
991     /var
974     /tmp
205     /boot
179     /opt
...

```

i use 3.16.0-34-generic #45~14.04.1-Ubuntu SMP Tue Mar 24 11:14:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux, lvm with 2 mirrored ssd drives, encrypted ( partitions created with ubuntu installation assistant )

```
 fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003cd9a


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   976771071   488384512   fd  Linux raid autodetect


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044be4


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   976771071   488384512   fd  Linux raid autodetect


Disk /dev/md0: 500.0 GB, 499971325952 bytes
2 heads, 4 sectors/track, 122063312 cylinders, total 976506496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf326


    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1            2048      487423      242688   83  Linux
/dev/md0p2          489470   976504831   488007681    5  Extended
/dev/md0p5          489472   976504831   488007680   83  Linux


Disk /dev/mapper/md0p5_crypt: 499.7 GB, 499717767168 bytes
255 heads, 63 sectors/track, 60753 cylinders, total 976011264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/md0p5_crypt doesn't contain a valid partition table


Disk /dev/mapper/lvm+ssd-root: 439.7 GB, 439709859840 bytes
255 heads, 63 sectors/track, 53458 cylinders, total 858808320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/lvm+ssd-root doesn't contain a valid partition table


Disk /dev/mapper/lvm+ssd-swap: 60.0 GB, 60003713024 bytes
255 heads, 63 sectors/track, 7295 cylinders, total 117194752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/lvm+ssd-swap doesn't contain a valid partition table



```

---

### Post by nerdtron on 2015-07-09
Have you tried to reboot? sometimes you can encounter that the filesystem does not update it's free space even if you deleted some of the big disk consuming files.

---

