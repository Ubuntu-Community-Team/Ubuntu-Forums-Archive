---
title: "The way ubuntu configures filesystem"
date: 2008-02-01
forum: General Help
---

### Post by plainwhitetoast on 2008-02-01
the output of "mount" command on my fresh new ubuntu 7.10 system is:

-------------------------------------- BEGIN --------------------------------------
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
---------------------------------------- END ----------------------------------------

while the contents of "/etc/fstab" are:

-------------------------------------- BEGIN --------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee /        ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
---------------------------------------- END ----------------------------------------

so as you can see my system uses sysfs, tmpfs in many places like "/var/run", "/var/lock" and so on, but all these mountpoints are NOT configured in /etc/fstab, so the question is: where are they configured?

---

### Post by PinkFloyd102489 on 2008-02-01
Probably by kernel modules or something a normal user cant touch. Most of those are temporary filesystems, like the lrm on libmodules volatile.

---

### Post by plainwhitetoast on 2008-02-01
so what if i don't like to use, for example, tmpfs on "/var/lock" or if I'd like to use tmpfs for other dirs like "/tmp"?
There must be a way to configure such things: man, it's linux! ;-)

...just I'm wondering *WHERE* those settings are...

---

### Post by PinkFloyd102489 on 2008-02-01
I personally dont know, but most programs utililize /tmp anyway. I know that Firefox caches flash videos (YouTube) into /tmp. That's how I download and encode my own videos. :-P

---

### Post by plainwhitetoast on 2008-02-01
yes right, that's why I'd like to use tmpfs on that dir, because despite of all other dirs that use tmpfs, /tmp is NOT configured to use that by default! :-)

---

### Post by pointone on 2008-02-01
```
sudo mount -t tmpfs /var/lock /var/lock
```

---

