---
title: "not mounting my other HDD"
date: 2007-11-11
forum: General Help
---

### Post by posterboy on 2007-11-11
Well, I read through the threads, nothing there for me. I upgraded from 7.04 to 7.10 this morning, some issues, solved a few already. This one is a killer! I have 2 HDD's in here, before the upgrade they showed up as hda and hdc, hdb being my DVD. I had hdc mounting into a folder in my user home dir. Worked great. NOW, however, it won't mount, and is not even seen. Here's my mount:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-386/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

Why does this show SDA? It's mounted, obviously, but there is NO /dev/hdc, or /dev/sdc anything available to mount my other drive. HELP! and thanks

---

### Post by posterboy on 2007-11-11
Bump

I think I probably need to do a mknod, but that's complex, and I don't understand it from the man page. 
Is that what I need to do, and can someone help me with that, please? 
I have no /dev/hd* anything, only sd* and that's not right, I have no scsi drives, only IDE's.

---

### Post by geirha on 2007-11-11
no, ubuntu uses udev, so mknod should never be used.

What does ```
sudo fdisk -l
``` say?

/dev/sd? are also used for SATA drives

---

### Post by posterboy on 2007-11-11
Thank you. Here we go:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004b1f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000382ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9733    78180291   83  Linux

Actually, that's interesting, let me see if I can mount sdb. 
WOW! It mounts. What the heck? My DVD has moved to scd0 now. All this as a result of the upgrade. ALL my drives have moved around, but at least we found them. 
I guess I can edit fstab to show sdb1 and it will mount at boot, right?
Thank you for your help!

---

### Post by geirha on 2007-11-11
It's a good idea to specify it by UUID (universally unique identifier) instead of device node in fstab. Then it won't matter if it "moves around" again. One way of finding the uuid is ```
ls -l /dev/disk/by-uuid/ | grep sdb1
``` Then add it to fstab with something like: ```
UUID=01234567-89ab-cdef-0123-456789abcdef /media/disk           ext3    defaults        0       2
```

---

### Post by posterboy on 2007-11-11
Done, and I thank you sir.

---

