---
title: "Help me fix my file system corruption (+ fstab problem)"
date: 2007-09-16
forum: General Help
---

### Post by xghstst0riesx on 2007-09-16
Basically I think my file system is somewhat corrupted. I can't run fsck because I can't unmount the drive - I get the error "mount disagrees with fstab". 

Some background. I'm pretty sure my problems began after installing a utility in Windows that lets me read my ext3 partition. After booting into ubuntu again I started to get file system errors on start up and fsck was run a few times. Everything else seems to be working except for MySQL and based on the errors I suspect it's the file system. So what should I do? I am planning on running fsck again with the ext3 option (I'm not sure if that was the case before when it ran automatically on start .) This is what my fstab looks like :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bd01eabe-1a00-445c-8952-fcd41d500535 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D6-0511  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=86A099F6A099ED45 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=66aa1d35-f03e-4bdc-9b59-1cc0349b7cec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
The partition in question is /dev/sda3. Is there something wrong with my fstab? Is there another solution to my problem? thanks.

---

### Post by dcstar on 2007-09-18
> **xghstst0riesx said:**
> Basically I think my file system is somewhat corrupted. I can't run fsck because I can't unmount the drive - I get the error "mount disagrees with fstab". 

Some background. I'm pretty sure my problems began after installing a utility in Windows that lets me read my ext3 partition. After booting into ubuntu again I started to get file system errors on start up and fsck was run a few times. Everything else seems to be working except for MySQL and based on the errors I suspect it's the file system. So what should I do? I am planning on running fsck again with the ext3 option (I'm not sure if that was the case before when it ran automatically on start .) This is what my fstab looks like :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=bd01eabe-1a00-445c-8952-fcd41d500535 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D6-0511  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=86A099F6A099ED45 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=66aa1d35-f03e-4bdc-9b59-1cc0349b7cec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
The partition in question is /dev/sda3. Is there something wrong with my fstab? Is there another solution to my problem? thanks.

Possibly you have changed the UUID of the partition, run the **mount** command and see if it agrees with your fstab file.

---

### Post by xghstst0riesx on 2007-09-18
This is the output of "mount". It doesn't contain any information about the UUID.

```

/dev/sda3 on / type ext3 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

---

### Post by oldos2er on 2007-09-18
I got this once when the UUID changed after installing another distro on a different partition.
 If you're using Gnome, go to Places, Home Folder. Then click File System (should be in the left hand column), dev, disk, by-uuid. You can check the UUID number of your sda3 partition there. Running fsck won't change it, you have to do it manually.

---

### Post by BLTicklemonster on 2007-09-18
Ya got any fstab~ files laying around in /etc? Compare them with what you have now.

And why does his / look the way it does with remount and all? Mine looks totally different:

# /dev/hda7
UUID=b273732b-419d-46f4-8433-8b034922cc4e /               reiserfs notail          0       1

---

