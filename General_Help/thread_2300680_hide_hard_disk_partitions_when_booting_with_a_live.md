---
title: "hide hard disk partitions when booting with a live usb ubuntu"
date: 2015-10-27
forum: General Help
---

### Post by fdo2 on 2015-10-27
I'm configuring a ubuntu 14.04 LTS in a usb stick. I want to use it in some computers, but I dont' want the partitions on these disk to appear and can be mounted from the os in the usb stick
for now the only way I have seen is to put a line in /etc/fstab with some errors in order to prevent them to be mounted. I guess something better should be done, but I can't find it.

any help?

regards

---

### Post by ajgreeny on 2015-10-27
I think that any user of a live system can do almost anything when the live OS is running as that user can easily run with root permissions and rights and therefore can mount any partition that is mountable if the right command are known; I am not aware of a way to avoid that using fstab from the live OS but maybe a custom live iso image that does not include the ability to raise the user's use of root might do it.  I have no idea of exactly how that could be done.

Can I ask why you want to do this; is it for a particular purpose or just an academic exercise?

---

### Post by fdo2 on 2015-10-28
I'm going to use a ubuntu on a pendrive in which I've installed [GNU Radio]("http://gnuradio.org/redmine/projects/gnuradio/wiki")  to work in class with my students.  I know they are not going to break anything on purpouse, but they may break something  by accident.  If they boot the OS with the usb stick and the 3 partitions we have on disk appear on the side bar and they mount them just by clicking, with root privileges is very likely they may break something by accident. So i would like to avoid it. 


> **ajgreeny said:**
> I think that any user of a live system can do almost anything when the live OS is running as that user can easily run with root permissions and rights and therefore can mount any partition that is mountable if the right command are known; I am not aware of a way to avoid that using fstab from the live OS but maybe a custom live iso image that does not include the ability to raise the user's use of root might do it.  I have no idea of exactly how that could be done.

Can I ask why you want to do this; is it for a particular purpose or just an academic exercise?

---

### Post by sudodus on 2015-10-28
Maybe you can install GNU radio so that it is available from an installed system's ***guest account***. You can install a system into a USB pendrive (like you install a system into an internal drive.

If you remove the internal drive before the installation, it will be easier, and you eliminate the risk to damage the installed system in the internal drive.

An installed system on a USB drive is portable if you avoid proprietary drivers. You may want to add the mount option noatime in fstab to avoid excessive wear. You may also want to turn off journaling in the root file system

---

### Post by fdo2 on 2015-10-29
> **sudodus said:**
> Maybe you can install GNU radio so that it is available from an installed system's ***guest account***. You can install a system into a USB pendrive (like you install a system into an internal drive.

I have installed it in a USB pendrive

> 
If you remove the internal drive before the installation, it will be easier, and you eliminate the risk to damage the installed system in the internal drive.

Well I've done the installation in a VMWare virtual machine with no disk configured, anyway I din't mind damaging the "installed system" ;-)
The problem is that I'm going to clone the USB pendrive to 14 pendrives and use them on different computers and I don't want to damage them, so I would like to avoid damaging on accident.
I have been using one usb persistent live system for gnu radio, [here]("http://files.ettus.com/liveusb/2.2/"), and it worked the way I wish to make my new usb pendrive to work: I was not able to mount any filesystem on the host computer (had disk partitions, DVD, pendrives, etc) 

> 
An installed system on a USB drive is portable if you avoid proprietary drivers. You may want to add the mount option noatime in fstab to avoid excessive wear. You may also want to turn off journaling in the root file system

I guess noatime option should be great, the problem is that my filesystem is not mounted in /etc/fstab....... or maybe it is.....  if /cow refers to sddr2 merged with sddr3.... then I have to change setting on /cow?

```

root@ubuntu:/home/ubuntu# mount
/cow on / type overlay (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sddr2 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sddr3 on /media/ubuntu/casper-rw type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sr0 on /media/ubuntu/Plop Boot Manager 5.0.14 type iso9660 (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)
/dev/sddr1 on /media/ubuntu/ubu1404364 type vfat (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

```


```

root@ubuntu:/home/ubuntu# cat /etc/fstab
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

The pendrive was created with mkusb, it has a sda1 vfat filesystem, a sda2 ext4 filesystem wich contains the .iso of ubuntu and a sda3 wich contains the ext4 persistent casper-rw filesystem.

**eddited:   Any change in /etc/fstab is lost on reboot

---

### Post by sudodus on 2015-10-30
> **fdo2 said:**
> [QUOTE=sudodus;13381149]Maybe you can install GNU radio so that it is available from an installed system's ***guest account***. You can install a system into a USB pendrive (like you install a system into an internal drive.

I have installed it in a USB pendrive

> 
If you remove the internal drive before the installation, it will be easier, and you eliminate the risk to damage the installed system in the internal drive.

Well I've done the installation in a VMWare virtual machine with no disk configured, anyway I din't mind damaging the "installed system" ;-)
The problem is that I'm going to clone the USB pendrive to 14 pendrives and use them on different computers and I don't want to damage them, so I would like to avoid damaging on accident.
I have been using one usb persistent live system for gnu radio, [here]("http://files.ettus.com/liveusb/2.2/"), and it worked the way I wish to make my new usb pendrive to work: I was not able to mount any filesystem on the host computer (had disk partitions, DVD, pendrives, etc) 
[/quote]
I see
> 
[QUOTE]
An installed system on a USB drive is portable if you avoid proprietary drivers. You may want to add the mount option noatime in fstab to avoid excessive wear. You may also want to turn off journaling in the root file system

I guess noatime option should be great, the problem is that my filesystem is not mounted in /etc/fstab....... or maybe it is.....  if /cow refers to sddr2 merged with sddr3.... then I have to change setting on /cow?
[/quote]
/cow indicates that you have a ***persistent live*** system, but noatime is intended only for ***installed*** systems, (similar to installed into an internal drive, but to a USB flash drive). See the following link for more details,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)
> 
```

root@ubuntu:/home/ubuntu# mount
/cow on / type overlay (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sddr2 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sddr3 on /media/ubuntu/casper-rw type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sr0 on /media/ubuntu/Plop Boot Manager 5.0.14 type iso9660 (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)
/dev/sddr1 on /media/ubuntu/ubu1404364 type vfat (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

```


```

root@ubuntu:/home/ubuntu# cat /etc/fstab
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

The pendrive was created with mkusb, it has a sda1 vfat filesystem, a sda2 ext4 filesystem wich contains the .iso of ubuntu and a sda3 wich contains the ext4 persistent casper-rw filesystem.

**eddited:   Any change in /etc/fstab is lost on reboot

*ajgreeny* and I see a security problem with a persistent live system. A live system is made so that it can mount and read internal drives, and the default user gets superuser privileges without any password. Even if you make some work-around to turn it off in the persistent live system, a clever user might be able to boot into a live-only system and use these superuser privileges.

This is why I suggested an installed system, where the users can only run in a guest account.

---

