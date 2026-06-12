---
title: "Aufs not reporting correct free space"
date: 2013-10-19
forum: General Help
---

### Post by kayot2 on 2013-10-19
I made a script for mounting a disk pool with aufs;

```
d0="/media/Storage0"
d1="/media/Storage1"
d2="/media/Storage2"
d3="/media/Storage3"
d4="/media/Storage4"

mount -t aufs -o br=$d0=rw:$d1=rw:$d2=rw:$d3=rw:$d4=rw -o create=mfs none pool
```

It works fine (though I wouldn't mind putting it into fstab instead) but the reported free space is only the free space on Storage1.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1        36G  2.1G   32G   7% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            489M  4.0K  489M   1% /dev
tmpfs           100M  2.0M   98M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            498M     0  498M   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda1       1.9T  402G  1.5T  22% /media/Storage0
/dev/sdb1       1.9T  173G  1.7T  10% /media/Storage1
/dev/sdd1       293G   64M  278G   1% /media/Storage2
/dev/sde1       294G   65M  279G   1% /media/Storage3
none            1.9T  402G  1.5T  22% /media/pool
```

Storage4 is the remainder of /dev/sdc1

 I was reading about using sum, but I have no idea how to do that, nor does google.

```
sum   df(1)/statfs(2) returns the total number of blocks and inodes of all branches. Note that there are cases that systemcalls may return ENOSPC, even if df(1)/statfs(2) shows that aufs has some free space/inode.
```

How do I get aufs to show the correct free space?

Edit:

Paco on The Geek Stuff forums told me what I was doing wrong. The answer  is simple and I overlooked it multiple time. The pooling line should  read:

```
mount -t aufs -o br=$d0=rw:$d1=rw:$d2=rw:$d3=rw:$d4=rw -o create=mfs _**-o sum**_ none pool
```

That merges the directorys correctly and reports the correct free space. Problem Solved!

---

