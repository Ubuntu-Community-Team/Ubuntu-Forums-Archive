---
title: "Folder permissions issue"
date: 2007-10-05
forum: General Help
---

### Post by donaldd on 2007-10-05
I have just setup a computer so my wife and children can use it. I have created a spare 200 gig partition so we can all share music films etc, please can someone tell me how to setup so we can all write and read to the data partition,  i am struggling with permission issues.

Thanks in advance.

---

### Post by yabbadabbadont on 2007-10-05
With the partition mounted, run in a terminal window
```
mount
ls -l /
ls -l /media

```
And post the results.  I'm specifically looking for the mount point of the data partition you created, so list it if you know what it is called and where it is mounted please.

---

### Post by donaldd on 2007-10-08
Let me know if you need anything else, the drive I am trying to share is dstuff.

donald@amber:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda4 on /dstuff type ext3 (rw)
/dev/hda2 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
donald@amber:~$ ls -l /
total 88
drwxr-xr-x   2 root root  4096 2007-09-29 16:29 bin
drwxr-xr-x   3 root root  4096 2007-09-29 16:33 boot
lrwxrwxrwx   1 root root    11 2007-09-29 14:35 cdrom -> media/cdrom
drwxr-xr-x  12 root root 13760 2007-10-08 18:36 dev
drwxr-xr-x   4 root root  4096 2007-09-29 23:10 dstuff
drwxr-xr-x 121 root root 12288 2007-10-08 18:36 etc
drwxr-xr-x   8 root root  4096 2007-10-05 22:23 home
drwxr-xr-x   2 root root  4096 2007-04-15 12:48 initrd
lrwxrwxrwx   1 root root    33 2007-09-29 16:34 initrd.img -> boot/initrd.img-2.6.20-16-generic
lrwxrwxrwx   1 root root    33 2007-09-29 14:44 initrd.img.old -> boot/initrd.img-2.6.20-15-generic
drwxr-xr-x  16 root root  4096 2007-09-29 16:30 lib
drwx------   2 root root 16384 2007-09-29 14:32 lost+found
drwxr-xr-x   4 root root  4096 2007-10-08 18:35 media
drwxr-xr-x   2 root root  4096 2007-04-12 10:11 mnt
drwxr-xr-x   2 root root  4096 2007-04-15 12:48 opt
dr-xr-xr-x 111 root root     0 2007-10-08 18:35 proc
drwxr-xr-x  12 root root  4096 2007-09-29 23:41 root
drwxr-xr-x   2 root root  4096 2007-09-29 16:30 sbin
drwxr-xr-x   2 root root  4096 2007-04-15 12:48 srv
drwxr-xr-x  11 root root     0 2007-10-08 18:35 sys
drwxrwxrwt  11 root root  4096 2007-10-08 18:44 tmp
drwxr-xr-x  12 root root  4096 2007-09-29 16:13 usr
drwxr-xr-x  15 root root  4096 2007-04-15 13:01 var
lrwxrwxrwx   1 root root    30 2007-09-29 16:34 vmlinuz -> boot/vmlinuz-2.6.20-16-generic
lrwxrwxrwx   1 root root    30 2007-09-29 14:44 vmlinuz.old -> boot/vmlinuz-2.6.20-15-generic
donald@amber:~$ ls -l /media
total 8
lrwxrwxrwx 1 root root    6 2007-09-29 14:34 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-09-29 14:34 cdrom0
lrwxrwxrwx 1 root root    7 2007-09-29 14:35 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-09-29 14:35 floppy0

---

### Post by nick_h on 2007-10-08
Add a new group in System->Administration->Users and Groups.
Then make the users members of the group.

When you have done this you can give files and directories group permissions.

---

### Post by yabbadabbadont on 2007-10-08
No need to create a new group, unless you have some users that you don't want to have access to the drive.  If all local users should be able to access it, then just run the following in a terminal window:
```
sudo chgrp users /dstuff
sudo chmod u+w /dstuff

```
Now all local users, who are members of the users group (they are by default), will have full access to /dstuff.

---

### Post by donaldd on 2007-10-09
Excellent thank you the answer is quite simple why didn't I think of it :-)

---

### Post by nick_h on 2007-10-09
True.  If you want all users to access the directory then you can use the existing group.

---

### Post by exchequer598 on 2007-10-21
I have tried various methods of changing permissions, but still I am not able to write to any of the partitions that I use in Windows XP. I tried the mount command and this is what I got ->

> prasannah@home:~$ mount
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type fuseblk (ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hda6 on /media/hda6 type fuseblk (ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hdb5 on /media/hdb5 type fuseblk (ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hdb6 on /media/hdb6 type fuseblk (ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hdb7 on /media/hdb7 type fuseblk (ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hda5 on /media/hda5 type vfat (rw,noexec,nosuid,nodev,fmask=0133,dmask=0022,uid=1000,gid=1000)
/dev/hda7 on /media/hda7 type vfat (rw,noexec,nosuid,nodev,fmask=0133,dmask=0022,uid=1000,gid=1000)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/hdb8 on /media/Junk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

I need to freely write/modify the files and folders in these drives too. Please HELP!!
One specific thing that I want to do is move the files I MP3s I downloaded using FrostWire (which are saved in /usr/prasannah/share folder) to my partition dedicated for music (hdb7)

P.S.: I am using the diskmounter script to automatically mount all drives on startup.

---

### Post by nick_h on 2007-10-23
You need to mount the device as *rw* rather than *ro* if you want to write to it.

---

