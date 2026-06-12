---
title: "Installing LVM on a software raid0 partition"
date: 2015-07-04
forum: General Help
---

### Post by jakob5 on 2015-07-04
Hello.

I have a remote server running, that comes pre installed this way:
```
ls /dev | grep sd
sda
sda1
sda2
sda3
sda4
sda5
sdb
sdb1
sdb2
sdb3
sdb4
sdb5
```

```
ls /dev | grep md
md0
md1
md2
md3
```

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/md2         11G  2.4G  8.4G  23% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.8G   12K  7.8G   1% /dev
tmpfs           1.6G  556K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.8G     0  7.8G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/md1        488M   69M  419M  15% /boot
/dev/md3        5.4T  6.2G  5.4T   1% /home

```

I want to split the big /home partition into smaller partitions, and it seems LVM is the tool for the task.
Specifically, i want to end up with a /data directory which holds 3-4 mounted partitions.
I tried to do it a couple of weeks ago, and ended up with a system that wouldn’t start, which resulted in a reinstall.

I have been looking all over the internet for a clue on how to combine the software raid, and LVM but i cant seem to find anything im comfortable using (I'm abit carefull, after the last crash).
I have no data on the server at the moment, because i want to resolve this issue first.

Can anyone point me in the right direction?

---

### Post by jakob5 on 2015-07-06
I have been working on this for a while, and i think i got it, though not with LVM.

I ended up deleting the partition table on /dev/md3, creating 4 new md3p1, md3p2 md3p3 and md3p4 using gparted.
I have now recreated my /home directory, and succesfully mounted all drives to their respective folders.

Now i got a question about the fstab configuration.

What i did was edit to this:
```
proc /proc proc defaults 0 0
/dev/md/0 none swap sw 0 0
/dev/md/1 /boot ext3 defaults 0 0
/dev/md/2 / ext4 defaults 0 0
/dev/md3p1 /home ext4 defaults 0 0
/dev/md3p2 /data/rtorrent ext4 defaults 0 0
/dev/md3p3 /data/plex ext4 defaults 0 0
/dev/md3p4 /data/software ext4 defaults 0 0
```

Will this work?

---

