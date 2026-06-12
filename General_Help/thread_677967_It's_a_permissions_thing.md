---
title: "It's a permissions thing"
date: 2008-01-25
forum: General Help
---

### Post by happypig on 2008-01-25
I just installed 7.10 dual booting. I want to be able to fully access My Documents on a fat32 partition but I can only read some directories and not modify.
I've tried 

[INDENT]sudo chmod 777 sda5 [/INDENT]

and 
[INDENT]
sudo chmod -R 777 sda5[/INDENT]

from a terminal (in /media)  but the permissions do not change. I thought it might be mounted read-only so I ran mount and it gave 
[INDENT]
gary@gary-desktop-ubuntubox:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
[/INDENT]

Where am I going wrong ?

---

### Post by taurus on 2008-01-25
I would edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the current entry for /dev/sda5 with this.

```
/dev/sda5   /media/sda5   vfat   defaults,umask=000   0   0
```

You don't have to remove the old entry for /dev/sda5.  Just put a # in front of it to comment it out in case you need it later.

Then reboot.

---

### Post by jeffus_il on 2008-01-25
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=123835](http://ubuntuforums.org/showthread.php?t=123835)

---

### Post by happypig on 2008-01-25
@ taurus - thanks, that did the trick

---

