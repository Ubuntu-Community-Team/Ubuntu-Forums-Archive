---
title: "External USB HDD NTFS Problem"
date: 2006-07-13
forum: General Help
---

### Post by _Alien__ on 2006-07-13
I have an USB HDD 120gb when i plug in Ubuntu find and mount it, but in reiserFS.


~$ mount

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda1 on /media/usbdisk type reiserfs (rw,nosuid,nodev)

~$ fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15504   117210208+   7  HPFS/NTFS

When i umount whit root and mount next, he mount in NTFS. So the problem is when he mount automatic when i plugin.

What i need to do to plug in automatic in NTFS instead reiserFS?

---

