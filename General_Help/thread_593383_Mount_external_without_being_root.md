---
title: "Mount external without being root"
date: 2007-10-27
forum: General Help
---

### Post by mlat on 2007-10-27
I was working on getting an external drive working. In a nutshell, everything works. However, it won't mount on login, and when I try to access it it tells me permission denied. I have to mount it in terminal manually if I want to use it.

This is only a real problem because this is not my computer, it's owned by people who aren't as technically knowledgeable. Believe it or not the step of mounting it would be a problem for them, even if its on some shell script they run or something and enter their password. I need it to mount on startup and properly.

Problem:
```
mike@latop:~$ mount /media/lat
Error opening partition device: Permission denied
Failed to mount '/dev/ndas-00702676-0p1': Permission denied

```


/etc/fstab:
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=325b13b3-1461-490f-9a6b-ad04bdf98afe /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=025832E25832D3DF /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=01c6f336-9ad5-4fde-a7c0-54bb666d62cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/ndas-00702676-0p1 /media/lat ntfs user,defaults,umask=007,gid=46 0 1

```

---

### Post by frederic.tardif on 2008-04-12
i am having the same issue with a ndas drive too. Any help about it?

---

