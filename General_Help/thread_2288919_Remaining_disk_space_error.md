---
title: "Remaining disk space error"
date: 2015-07-30
forum: General Help
---

### Post by ibod on 2015-07-30
Hi All,

I have ubuntu 14.04 32bit

I am getting repeated "Low Disk Space" warnings that state :-

The volume "home" has only 593 MB disk space remaining.

When I look in gparted I can see I have loads of space :-

```

Partition       File System     Size            Used          Unused      Flags
/dev/sda1     ext4              10.06 GiB     5.07 GiB       4.99 GiB   boot
/dev/sda2     ext4              60.72 GiB     6.44 GiB     54.28 GiB    
/dev/sda3     linux-swap       5.91 GiB     0.00 B         5.91 GiB    

```

df-h and df -i outputs :-

```

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        19G  7.9G  9.9G  45% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.4G  8.0K  1.4G   1% /dev
tmpfs           278M  1.5M  277M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.4G  352K  1.4G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sdb2        29G   27G  566M  98% /home

$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sdb1      1250928 408310  842618   33% /
none            218185      2  218183    1% /sys/fs/cgroup
udev            213385    514  212871    1% /dev
tmpfs           218185    592  217593    1% /run
none            218185      3  218182    1% /run/lock
none            218185      7  218178    1% /run/shm
none            218185     26  218159    1% /run/user
/dev/sdb2      1908736  62044 1846692    4% /home
daniel@daniel-IMEDIA-2426:~$ 


```

Properties window for home :-
```

Name 
Type Folder (inode/director)
Contents  16,471 items, totalling 26.0 GB
Location  /home
Free space 592.3MB

```

Why does gparted report the partition almost empty and the system report that home it almost full 
is the drive broken or corrupt ?

Thanks for any help you can give

---

### Post by oldfred on 2015-07-30
You showed sda as your partitions, but /home is on sdb2 and is 98% full. 

In gparted, upper right you can change drives to see sdb drive. It only shows one drive at a time.

---

### Post by ibod on 2015-07-30
Silly mistake 

Thanks

---

### Post by oldfred on 2015-07-30
Sometimes little things not not obvious. :)

---

