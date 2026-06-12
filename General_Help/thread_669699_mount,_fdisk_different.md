---
title: "mount, fdisk different"
date: 2008-01-16
forum: General Help
---

### Post by dbarbour on 2008-01-16
WTF is this? *mount* reports that /dev/sda1, a 320 GB HDD with absolutely nothing on it, is mounted on /. Meanwhile, /dev/sdb contains the actual Linux install and *mount* says it's not even mounted. Can someone explain what is going on here?```
dbarbour@dbarbour-server:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
dbarbour@dbarbour-server:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d8f261f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062abd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9363    75208266   83  Linux
/dev/sdb2            9364        9729     2939895    5  Extended
/dev/sdb5            9364        9729     2939863+  82  Linux swap / Solaris
dbarbour@dbarbour-server:~$ 

```

---

### Post by geirha on 2008-01-16
What does "df -h" say?

---

