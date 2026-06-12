---
title: "My uber 300gb hard drive that linux doesnt like"
date: 2006-07-07
forum: General Help
---

### Post by Linkhiei on 2006-07-07
Hello. I've got a 300gb(NTFS SATA) hard drive with no operating system, just video files (anime ^_^) and it just doesnt want to mount. I've gotten my 200gb NTFS SATA drive to mount and it has windows on it. When i enter this command: (sdb being the 300gb, /media/anime being the mount location)

sudo mount /dev/sdb /media/anime/ -t ntfs -o nls=utf8,umask=0222

i get the following:

"mount: /dev/sdb already mounted or /media/anime/ busy"

When I unmount the drive it tells me that it is already unmounted, so i try to mount the drive to a different folder but it says the same error message. Could anyone help me? ](*,)

---

### Post by simonn on 2006-07-07
What does the command:

```

$ mount

```

return?

---

### Post by Linkhiei on 2006-07-07
/dev/hdc1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-686/volatile type tmpfs (rw)
/dev/sda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222)

---

### Post by simonn on 2006-07-07
Hmmm... Are you sure it is sdb, not sdb1?

---

### Post by Linkhiei on 2006-07-07
>.< that was EXACTLY the problem, once i mounted it as sdb1 it worked perfectly, thanks alot for ur help! :)

---

