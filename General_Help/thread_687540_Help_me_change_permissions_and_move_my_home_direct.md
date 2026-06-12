---
title: "Help me change permissions and move my home directory"
date: 2008-02-04
forum: General Help
---

### Post by madhatter64 on 2008-02-04
I am running Ubuntu on VMware. I have added a 39 gig virtual disk which is now available only to root or superuser. 

What I want is to change the permissions on the new partition to my user, then move my current home directory to the new partition. 

Help?

Thanks

---

### Post by jan quark on 2008-02-04
please run 

```
mount 
```
```

sudo fdisk -l
```

this will give us information about the new virtual disk

permissions to file systems  that are based on fat32 and ntfs can be added only temporally for the mounting time

---

### Post by madhatter64 on 2008-02-04
[QUOTE=jan quark;4268000]please run 

```
mount 
```
Result is:

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
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
/dev/scd0 on /media/cdrom0 type udf (rw,nosuid,nodev,user=bagside)
/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev)


sudo fdisk -l

The result is:

Disk /dev/sda: 6442 MB, 6442450944 bytes
255 heads, 63 sectors/track, 783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e613

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         578     4642753+  83  Linux
/dev/sda2             737         783      377527+  82  Linux swap / Solaris
/dev/sda3             579         736     1269135   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000549d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5221    41937651   83  Linux

---

