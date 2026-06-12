---
title: "Problems with mounting disks &amp; usb flash"
date: 2006-10-16
forum: General Help
---

### Post by Orion2000za on 2006-10-16
I have a strange problem since a week or so. I am running Kubuntu 6.06.1 and have a disk partitioned in several "bits" like /, Home and swap. There is also an ntfs partition and a vfat (small rescue thing).

Now if I go to "Storage Media" and click on any of the ntfs or vfat I get the following message;
"Could not mount device. The reported error was: mount: /dev/sda2 already mounted or /media/sda2 busy. mount: according to mtab, /dev/sda2 is already mounted on /media/sda2"

More or less the same error happens if I insert a USB flash memory or a USB camera.
In all cases I can get around it by "going root" and use eg Krusader in root mode. I can then access the disk/usb/camera.

but a while ago I just accessed these no problems and when a USB or camera was inserted I could access as "a normal user".

Anyone has ideas?

Sinclair

---

### Post by Orion2000za on 2006-10-17
> **Orion2000za said:**
> I have a strange problem since a week or so. I am running Kubuntu 6.06.1 and have a disk partitioned in several "bits" like /, Home and swap. There is also an ntfs partition and a vfat (small rescue thing).

Now if I go to "Storage Media" and click on any of the ntfs or vfat I get the following message;
"Could not mount device. The reported error was: mount: /dev/sda2 already mounted or /media/sda2 busy. mount: according to mtab, /dev/sda2 is already mounted on /media/sda2"

More or less the same error happens if I insert a USB flash memory or a USB camera.
In all cases I can get around it by "going root" and use eg Krusader in root mode. I can then access the disk/usb/camera.

but a while ago I just accessed these no problems and when a USB or camera was inserted I could access as "a normal user".

Anyone has ideas?

Sinclair

Well, sorry to continue my own thread but no help this far. Have now discovered that inserting CD/DVD gives exactly the same problem. It comes up nicely on the desktop but try to access and the same error comes up. 
Anyone? Will soon have to give up and reinstall - and I am not too keen on that...

Sinclair

---

### Post by hvc123 on 2006-10-17
i think you must have things manually mounted in your /etc/fstab. 

because ubuntu uses automounts sounds like a conlfict. 
post your fstab and relevant /var/log/messages

---

### Post by Zeddicus on 2006-10-17
Do things clear up if you:

```
sudo /etc/init.d/dbus restart
```

I have had some minor issues in the past with HAL refusing to realize that things have been unmounted... just poking to see if you're having the same issue.

(if that cures the issue, you might want to look into upgrading to KDE 3.5.5 -- it seemed to fix my problem with that. :) )

---

### Post by Orion2000za on 2006-10-18
thanks for input! I tried restarting the dbus but no change.

Here is my fstab;
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sda3 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/sda6 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
/dev/sda1 /media/sda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/sda2 /media/sda2 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,user 0 1
/dev/sda5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

and my mtab with a usb device mounted (last line) but not avaiable unless you are root;
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-686/volatile tmpfs rw 0 0
/dev/sda6 /home ext3 rw 0 0
/dev/sda1 /media/sda1 vfat rw,utf8,umask=007,uid=0,gid=46 0 0
/dev/sda2 /media/sda2 ntfs rw,noexec,nosuid,nodev,nls=utf8,umask=007,uid=0,gid=46 0 0
/dev/sdb1 /media/sdb1 vfat rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0


as for messages in var/log.. hm I am not sure what is relevant there, too "deep in linux" for me. 

Sinclair

---

