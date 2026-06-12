---
title: "Ubuntu won't recognize my iPod!"
date: 2007-03-29
forum: General Help
---

### Post by Fireblend on 2007-03-29
It did yesterday, now whenever I connect it, it won't get mounted even tho it's in disk mode (with the "don't disconnect" screen). Any idea what could be causing this? I have Beryl installed, if it's of any help :confused: 

Edit: I just tried connecting another iPod and it won't work either. It works well on WIndows so I know that's not it.

Thanks in advance!

---

### Post by Fireblend on 2007-03-29
Damn, please help. I just did everything here:

[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

And it won't work.

This is my mtab file:

> /dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 fuse rw,nosuid,nodev,noatime,allow_other 0 0
/dev/hdb1 /media/hdb1 fuse rw,nosuid,nodev,noatime,allow_other 0 0
/dev/hdb2 /media/hdb2 fuse rw,nosuid,nodev,noatime,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

I'm supposed to find my iPod's mount point, but I don't know where that is in that text file >_< please help!!! Typing sudo dosfsck -a /dev/sdc2 does nothing.

/media/ipod already existed when I tried to create it, and when I added...

> /dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0 

... to the fstab file nothing happened.

Please, help! Is there some way I can reset all this stuff to start with that tutorial from zero? My iPod is listed on the device manager's list too. WHat am I doing wrong?!

---

### Post by justin whitaker on 2007-03-29
I had this issue with Edgy before....usually a reboot with the iPod attached fixed it. I think it has something to do with the kernel module not dropping when you pull the iPod manually without ejecting.

---

### Post by Fireblend on 2007-03-29
Nope, this isn't working. Please, someone help, I really need to use my iPod as an external harddrive.

---

