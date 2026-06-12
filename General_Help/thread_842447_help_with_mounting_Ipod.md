---
title: "help with mounting Ipod"
date: 2008-06-27
forum: General Help
---

### Post by blahfod on 2008-06-27
Okay guys,

I did something stupid. In order for me to correctly mount my Ipod to sync contacts through gtkpod I had to change the name of the Ipod. I couldn't figure out how to change the name of the ipod, but figured i could change the name of the mount point which will allow the scripts in gtkpod to find it. the original name of the ipod is Mikael's Ip, and thus it was mounting it to media/Mikael's Ip, I right clicked on the mounted icon on the desktop and changed the mount point to media/ipod, however, now it wont mount. I get an error about syntax usage, something along the lines of characters that i used in the mount point are not allowed. Now i can't figure out how to edit the mount point again to change it. Ubuntu still recognizes a connected ipod, but simply won't mount it. So i guess, how to I get this ipod mounted again, and better yet, how can i change the label/name of my ipod so I can avoid this in the future.

Secondly, is there a way to have rythmbox use the album art embedded in the mp3 tag instead of trying to get it from the web?

Thanks for the help.
Blahfod

---

### Post by unutbu on 2008-06-27
Try 

```
sudo mkdir /media/ipod
```

(I think the mount point might have to exist before the mount command will work).

If that doesn't work, please post
```

sudo fdisk -l
mount
```

---

### Post by blahfod on 2008-06-27
mkdir  /media/ipod/

didn't work, here is the output of those other commands:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11974    96181123+  83  Linux
/dev/hda2           11975       12161     1502077+   5  Extended
/dev/hda5           11975       12161     1502046   82  Linux swap / Solaris

mikael@mikael-laptop:~$ 


Disk /dev/hda: 100.0 GB, 100030242816 bytes

255 heads, 63 sectors/track, 12161 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x94e494e4


   Device Boot      Start         End      Blocks   Id  System

/dev/hda1   *           1       11974    96181123+  83  Linux

/dev/hda2           11975       12161     1502077+   5  Extended

/dev/hda5           11975       12161     1502046   82  Linux swap / Solaris
mikael@mikael-laptop:~$ mount
/dev/hda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/mikael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mikael)/dev/sda1 on /media/BLAHSTICK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
mikael@mikael-laptop:~$

---

### Post by unutbu on 2008-06-27
Is your ipod already mounted at /media/BLAHSTICK or is that some other device?

---

### Post by blahfod on 2008-06-27
blahstick is a usb memory stick
when i log in as the root, the ipod mounts no prob, but when i log in as user it doesn't, I have changed the ipod's volume name in windows to MIPOD and when plugged in Ubuntu recognizes it as that, but simply will not mout it. I need to find out how to change the properties of the mount is what I suspect.

BTW, thanks for helping out

---

### Post by blahfod on 2008-06-27
well it seems to have fixed itself. I loged in as root, mounted the ipod (this after having changed the volume label in windows) then switched to user and somehow it mounted it properly, i have now removed the changed mountpoint properties and hunky dory it works. Thanks for your time.

---

### Post by unutbu on 2008-06-27
Great. Glad to hear you fixed it!

---

