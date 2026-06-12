---
title: "Problems Moving usr and home to Flash Drive"
date: 2014-04-19
forum: General Help
---

### Post by spyke01 on 2014-04-19
Hi guys,
I'm running Ubuntu through crouton on a Chromebook 14 and since the system only has 18GB of space I want to put /home and /usr on a 32GB flash drive that I will have attached to the system. I have partitioned the flash drive so that it has a partition for each and have used this command to copy all the files to the proper partitions:

```
find . -depth -print0 | cpio --null --sparse -pvd /media/removable/PARTITION
```

I then edited /etc/fstab as follows:

```
UUID=9fee4259-6db6-43c6-b2e6-624b719eb56e /home          ext4    defaults        0
UUID=db1c7b5c-a41b-4196-8ce7-76b0b028bd44 /usr           ext4    defaults        0
```

The UUIDs matche the values from here:

```
spyke01@localhost:~/Downloads/wakfu$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Apr 19 16:43 224669a3-b991-450d-9988-a3629b676f29 -> ../../sda8
lrwxrwxrwx 1 root root 10 Apr 19 16:43 38304b06-9dad-409a-9224-e52d08aec1f5 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Apr 19 16:43 6bd3242b-3d58-479e-b127-d6100d1fe7f6 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 19 17:07 9DBB-0616 -> ../../sdb7
lrwxrwxrwx 1 root root 10 Apr 19 16:43 9fee4259-6db6-43c6-b2e6-624b719eb56e -> ../../sdb6
lrwxrwxrwx 1 root root 11 Apr 19 17:07 AFE1-B40B -> ../../sda12
lrwxrwxrwx 1 root root 10 Apr 19 16:43 db1c7b5c-a41b-4196-8ce7-76b0b028bd44 -> ../../sdb5

```

I've rebooted but it doesn't appear that the partitions have mounted to the /home and /usr locations. Here's the output showing this:
```
spyke01@localhost:~/Downloads/wakfu$ df
df: `/mnt/stateful_partition': No such file or directory
df: `/usr/share/oem': No such file or directory
df: `/mnt/stateful_partition/encrypted': No such file or directory
df: `/home/chronos': No such file or directory
df: `/sys/fs/cgroup/cpu': No such file or directory
df: `/sys/fs/cgroup/freezer': No such file or directory
df: `/var/run/debugfs_gpu': No such file or directory
df: `/home/.shadow/6c517dc388e0d347457c1f0a1f03a9221bf84c79/mount': No such file or directory
df: `/home/chronos/user': No such file or directory
df: `/home/user/6c517dc388e0d347457c1f0a1f03a9221bf84c79': No such file or directory
df: `/home/chronos/u-6c517dc388e0d347457c1f0a1f03a9221bf84c79': No such file or directory
df: `/home/root/6c517dc388e0d347457c1f0a1f03a9221bf84c79': No such file or directory
df: `/var/run/crw': No such file or directory
Filesystem                                                   1K-blocks    Used Available Use% Mounted on
rootfs                                                        10978244 5996712   4417208  58% /
/dev/root                                                     10978244 5996712   4417208  58% /
devtmpfs                                                       1992096     544   1991552   1% /dev
tmp                                                            1993232     264   1992968   1% /tmp
shmfs                                                          1993232   31192   1962040   2% /dev/shm
/dev/sda1                                                     10978244 5996712   4417208  58% /home
/dev/mapper/encstateful                                       10978244 5996712   4417208  58% /var
varrun                                                          398648      28    398620   1% /var/run
varlock                                                           5120       0      5120   0% /var/lock
media                                                         10978244 5996712   4417208  58% /media
/dev/sda1                                                     10978244 5996712   4417208  58% /usr/local
none                                                           1992096     544   1991552   1% /dev/pstore
/dev/sdb5                                                      9948012 1851048   7584964  20% /media/removable/usr
/dev/sdb6                                                      7110700 1984864   4757964  30% /media/removable/home
/dev/sdb7                                                     13891312       8  13891304   1% /media/removable/Data
/dev/sda1                                                     10978244 5996712   4417208  58% /
devtmpfs                                                       1992096     544   1991552   1% /dev
shmfs                                                          1993232   31192   1962040   2% /dev/shm
tmp                                                            1993232     264   1992968   1% /tmp
tmpfs                                                           398648      28    398620   1% /run
tmpfs                                                             5120       0      5120   0% /run/lock
varrun                                                         1993232      56   1993176   1% /var/host/dbus
varrun                                                         1993232      56   1993176   1% /var/host/shill
varrun                                                         1993232      56   1993176   1% /var/host/cras
/dev/mapper/encstateful                                        3237632   59628   3178004   2% /var/host/timezone
/dev/root                                                      1032088  949816     82272  93% /lib/modules/3.8.11
media                                                          1993232       0   1993232   0% /var/host/media
/dev/sdb5                                                      9948012 1851048   7584964  20% /var/host/media/removable/usr
/dev/sdb6                                                      7110700 1984864   4757964  30% /var/host/media/removable/home
/dev/sdb7                                                     13891312       8  13891304   1% /var/host/media/removable/Data
/home/.shadow/6c517dc388e0d347457c1f0a1f03a9221bf84c79/vault  10978244 5996712   4417208  58% /home/spyke01/Downloads
```

I don't know if the errors at the top give any info on the issue.

How do I fix this?

---

