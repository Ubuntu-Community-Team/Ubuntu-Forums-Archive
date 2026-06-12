---
title: "ubuntu doesnt see Linux-swap at startup"
date: 2008-05-14
forum: General Help
---

### Post by juan_valdez on 2008-05-14
I have a 1.5 GB Linux-swap as a logical partition inside an extended partition, and when i look at gparted, i have to right click and put swapon for it to be on, and when i restart my computer, it goes off.. what do i have to do to utilize my Linux-swap?

---

### Post by latna on 2008-05-14
Do you have a line for it in /etc/fstab? Something like this:
```
UUID=0f88f2db-7e3e-430e-85a1-fbd4bdfef451 none swap sw 0 0

```

---

### Post by wonk-o-matic on 2008-05-14
I won't be able to look at this again, for awhile, but to help the next person who looks in on this thread, paste the following into your next post: 

The output from the "mount" command.
The contents of your /etc/fstab file.

The swap partition isn't getting mounted at boot, and these items will probably result in a quick solution.

---

### Post by overdrank on 2008-05-14
> **juan_valdez said:**
> I have a 1.5 GB Linux-swap as a logical partition inside an extended partition, and when i look at gparted, i have to right click and put swapon for it to be on, and when i restart my computer, it goes off.. what do i have to do to utilize my Linux-swap?

HI and this link may help
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by juan_valdez on 2008-05-21
> **wonk-o-matic said:**
> I won't be able to look at this again, for awhile, but to help the next person who looks in on this thread, paste the following into your next post: 

The output from the "mount" command.
The contents of your /etc/fstab file.

The swap partition isn't getting mounted at boot, and these items will probably result in a quick solution.
ok heres what it says after i run mount

/dev/sda2 on / type ext2 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/sda3 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

and thats after i manually mounted it in gparted,
and the fstab says

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4c5936ca-58fd-4e6a-81eb-87b70fc71b59 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=02192BCF7B8448E2 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=4B6E-6BC0  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=a801769a-caf5-487c-8dfe-c180bb380482 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

