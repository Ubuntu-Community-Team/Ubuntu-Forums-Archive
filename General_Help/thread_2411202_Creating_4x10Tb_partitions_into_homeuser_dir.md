---
title: "Creating 4x10Tb partitions into /home/user dir?"
date: 2019-01-26
forum: General Help
---

### Post by pippo12 on 2019-01-26
Hi anyone could help me creating steps to mount 4x10tb hd to /home/user account?

Hardware data:
```
CPU1: Intel(R) Xeon(R) CPU E3-1271 v3 @ 3.60GHz (Cores 8)
Memory: 31905 MB
Disk /dev/sda: 10000 GB (=> 9314 GiB)
Disk /dev/sdb: 10000 GB (=> 9314 GiB)
Disk /dev/sdc: 10000 GB (=> 9314 GiB)
Disk /dev/sdd: 10000 GB (=> 9314 GiB)
Total capacity 36 TiB with 4 Disks
```


This is When logged in: 

```
root@Ubuntu-1604-xenial-64-minimal ~ # df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.2G  5.4M  3.2G   1% /run
/dev/sda3       2.0T  1.2G  1.9T   1% /
tmpfs            16G     0   16G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
/dev/sda2       488M   71M  392M  16% /boot
/dev/sda4       7.1T   89M  6.7T   1% /home
tmpfs           3.2G     0  3.2G   0% /run/user/0
root@Ubuntu-1604-xenial-64-minimal ~ #
```


```
root@Ubuntu-1604-xenial-64-minimal ~ # cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]

md0 : inactive sdc1[2](S) sdb1[1](S) sdd1[3](S)
      50282496 blocks super 1.2
```

```
md3 : inactive sdc4[2](S) sdb4[1](S) sdd4[3](S)
      26079258574 blocks super 1.2
```

```
md1 : inactive sdc2[2](S) sdb2[1](S) sdd2[3](S)
      1571280 blocks super 1.2
```

```
md2 : inactive sdc3[2](S) sdb3[1](S) sdd3[3](S)
      3167354880 blocks super 1.2
```

---

### Post by DuckHook on 2019-01-26
Welcome to the forums, pippo12.

I have edited your post to bring it into compliance with the Forum [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945"). Please use default fonts for ease of readability and post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

