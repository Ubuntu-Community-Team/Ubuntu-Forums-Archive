---
title: "Adding a menu option to Grub"
date: 2012-11-01
forum: General Help
---

### Post by oygle on 2012-11-01
Running 12.10 and it had 2 hard drives, grub menu would come up okay. I have just added a third hard drive with windows 95b on it.

How do I modify the grub menu to have the option of booting ot that 3rd HDD ?

> $ **mount**
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda6 on /home type ext3 (rw)
gvfsd-fuse on /run/user/peter/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=peter)
/dev/sdc5 on /media/W95_F type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdc1 on /media/W95_C type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdb1 on /media/8EFC2D0BFC2CEF61 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

/dev/sda is Kubuntu 12.10
/dev/sdb is Windows XP Pro
/dev/sdc is Windows 95b

Currently grub menu shows Ubuntu and Windows XP Pro options

Oygle

---

### Post by oygle on 2012-11-01
The extra menu option is there now ..

```
sudo update-grub
```

Oygle

---

