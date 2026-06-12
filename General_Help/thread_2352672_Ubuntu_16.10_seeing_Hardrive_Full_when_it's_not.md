---
title: "Ubuntu 16.10 seeing Hardrive Full when it's not"
date: 2017-02-14
forum: General Help
---

### Post by Serpentus on 2017-02-14
Hi;

Hope this is in the correct category.

I installed Ubuntu 16.10 on a 16GB USB stick.  Then I decided to move to an external e-SATA 80GB HDD. I did a clone with dd (dd if=/dev/sda of=/dev/sdb), then with the partion editor I moved and grew the partitions to their final state.

The problem is that Linux still see the drive as a 16GB instead of a 80GB when computing the freespace. This is the output of df:

```
df -h
Filesystem      Size  Used     Avail Use% Mounted on
udev             3,9G     0       3,9G   0% /dev
tmpfs            788M    9,5M  779M   2% /run
/dev/sdb2      11G      8,3G  1,9G  83% /
tmpfs            3,9G     25M   3,9G   1% /dev/shm
tmpfs            5,0M     4,0K  5,0M   1% /run/lock
tmpfs            3,9G     0      3,9G   0% /sys/fs/cgroup
/dev/sdb1      361M    67M   271M  20% /boot
/dev/sdb3      3,7G     3,5G  7,2M 100% /home
tmpfs           788M     0       788M   0% /run/user/119
tmpfs           788M     24K    788M   1% /run/user/1000
```

```
df -i:
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             1001955    598      1001357    1% /dev
tmpfs            1008196    848      1007348    1% /run
/dev/sdb2         709920   244946    464974   35% /
tmpfs            1008196     17       1008179    1% /dev/shm
tmpfs            1008196      6        1008190    1% /run/lock
tmpfs            1008196     16       1008180    1% /sys/fs/cgroup
/dev/sdb1          97536    300      97236       1% /boot
/dev/sdb3         249984   15038   234946      7% /home
tmpfs            1008196      5        1008191    1% /run/user/119
tmpfs            1008196     26       1008170    1% /run/user/1000
```

This is what the partition manager and device notifier report:
[ATTACH=CONFIG]273704[/ATTACH]

[ATTACH=CONFIG]273705[/ATTACH]

I hope there is a way to fix this without reinstalling everything again, my internet connection is VERY slow.... 

Thank you very much;
Serpentus

---

### Post by QIII on 2017-02-14
Moved to General Help

---

### Post by Serpentus on 2017-02-14
> **QIII said:**
> Moved to General Help

Thank you.

---

### Post by The Cog on 2017-02-14
I think that resizes2fs should be able to do an on-line resize of the filesystem to the actual partition size. 
Use "man resize2fs" to check for yourself, but I think these two should do it:
```
sudo resize2fs /dev/sdb2
sudo resize2fs /dev/sdb3
```

---

### Post by Serpentus on 2017-02-14
> **The Cog said:**
> I think that resizes2fs should be able to do an on-line resize of the filesystem to the actual partition size. 
Use "man resize2fs" to check for yourself, but I think these two should do it:
```
sudo resize2fs /dev/sdb2
sudo resize2fs /dev/sdb3
```

Thank you! It worked =D

```
df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             1001956    598   1001358    1% /dev
tmpfs            1008197    846   1007351    1% /run
/dev/sdb2        2741760 244956   2496804    9% /
tmpfs            1008197     10   1008187    1% /dev/shm
tmpfs            1008197      6   1008191    1% /run/lock
tmpfs            1008197     16   1008181    1% /sys/fs/cgroup
/dev/sdb1          97536    300     97236    1% /boot
/dev/sdb3        2080512  15170   2065342    1% /home
tmpfs            1008197      5   1008192    1% /run/user/119
tmpfs            1008197     22   1008175    1% /run/user/1000
```

```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3,9G     0  3,9G   0% /dev
tmpfs           788M  9,5M  779M   2% /run
/dev/sdb2        42G  8,3G   32G  21% /
tmpfs           3,9G   21M  3,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           3,9G     0  3,9G   0% /sys/fs/cgroup
/dev/sdb1       361M   67M  271M  20% /boot
/dev/sdb3        32G  2,6G   28G   9% /home
tmpfs           788M     0  788M   0% /run/user/119                                                                                                         
tmpfs           788M   20K  788M   1% /run/user/1000
```

---

### Post by Serpentus on 2017-02-14
Please mark as [SOLVED]... Sorry don't know how to do that.

Edit: Never Mind, already did

---

