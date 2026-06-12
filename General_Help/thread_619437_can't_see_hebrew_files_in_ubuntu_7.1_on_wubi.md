---
title: "can't see hebrew files in ubuntu 7.1 on wubi"
date: 2007-11-21
forum: General Help
---

### Post by [THE] KILLER on 2007-11-21
Hi,

I have a problem with hebrew files on my ntfs, I can't see them.
I know what is the problem, and normally I know how to fix it, by adding "nls=utf8" in the fstab file, but since wubi created the ntfs mounting I'm not sure what to do.

this is my fstab file:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,defaults,errors=remount-ro 0       1
/host/ubuntu/disks/home.disk /home           ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/host/ubuntu/disks/boot /boot none bind 0 0

``` 

10x, Adam.

---

### Post by [THE] KILLER on 2007-11-22
Hi again,

Another thing I thought would help, this is my mount table:
```

/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/home.disk on /home type ext3 (rw,loop=/dev/loop1)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=adam)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

---

