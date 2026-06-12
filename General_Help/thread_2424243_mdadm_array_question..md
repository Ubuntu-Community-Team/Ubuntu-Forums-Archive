---
title: "mdadm array question."
date: 2019-08-05
forum: General Help
---

### Post by rsteinmetz70112 on 2019-08-05
I have a machine with two mdadm arrays. One of teh 4 hard drives failed I replaced it added it to the array and it immediatel began rebuilding teh array.

Aftre it finished I checked it's status and got this

```
# cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdd[2] sdc1[0]
      976629760 blocks super 1.2 [2/2] [UU]
      bitmap: 0/8 pages [0KB], 65536KB chunk

md0 : active raid1 sda1[1] sdb1[0]
      976630464 blocks super 1.2 [2/2] [UU]
      bitmap: 3/8 pages [12KB], 65536KB chunk
```

Note that md1 shows disk sdd as drive 2 and sdc1 as drive 0. What happened to drive 1?

lsblk shows:
```
sdc                  8:32   0 931.5G  0 disk
&#9492;&#9472;sdc1               8:33   0 931.5G  0 part
  &#9492;&#9472;md1              9:1    0 931.4G  0 raid1
    &#9500;&#9472;system-root  252:1    0   150G  0 lvm   /system/root
    &#9500;&#9472;system-home  252:2    0 465.7G  0 lvm   /system/home
    &#9492;&#9472;system-xtra  252:3    0 315.7G  0 lvm   /system/xtra
sdd                  8:48   0 931.5G  0 disk
&#9500;&#9472;sdd1               8:49   0 931.5G  0 part
&#9492;&#9472;md1                9:1    0 931.4G  0 raid1
  &#9500;&#9472;system-root    252:1    0   150G  0 lvm   /system/root
  &#9500;&#9472;system-home    252:2    0 465.7G  0 lvm   /system/home
  &#9492;&#9472;system-xtra    252:3    0 315.7G  0 lvm   /system/xtra
```

There seem to be some confusion about sdd

---

