---
title: "mounting external WD HD (ntfs) with rw"
date: 2007-09-30
forum: General Help
---

### Post by damijim on 2007-09-30
Hello,
First off, I'm a linux newbie... well, I used slackware ten years ago, but memory fails.

I've been trying to figure out my problem for several days. I don't want to destroy the data on my Western Digital External HD (500GB (2 partitions, both NTFS)) connected via USB. Ubuntu, of course, auto-mounts it, but I want rw permissions to it.

I have tried umount and then mount in several ways, but it fails. Ultimately, I would like to add it to fstab. So, if anyone can help me mount it - or get it into fstab - I would appreciate it!

The external HD mounts as /dev/sdb1 and /dev/sdb5.

**[SIZE="3"]Here's some of my attempts/failures:[/SIZE]**

[INDENT]root@laptop:/# **mount**
[INDENT]/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=dami)
/dev/sdb1 on /media/External NTFS type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sdb5 on /media/External NTF 2 type ntfs (rw,nosuid,nodev,umask=222,utf8)
[/INDENT]
root@laptop :/# **umount /dev/sdb1**
root@laptop:/# **mount -t ntfs -o rw /dev/sdb1 /temp_external**
root@laptop:/# **cd /temp_external/**
root@laptop:/temp_external# ls
arcdeviceinfo  installs         p_nb535-install.exe  RECYCLER
autorun.inf    itunes My Music  $RECYCLE.BIN         System Volume Information
backups        newest           recycled             WD_mac_tools (2)
root@laptop:/temp_external# **mkdir bah**
**mkdir: cannot create directory `bah': Read-only file system[/INDENT]**

[SIZE="3"]**Another try:**[/SIZE]

[INDENT]root@laptop:/# **mount -t ntfs -o defaults /dev/sdb5 /temp_external/**
root@laptop:/# cd /temp_external/
root@laptop:/temp_external# ls
New Folder  $RECYCLE.BIN  System Volume Information
root@laptop:/temp_external# **mkdir test**
**mkdir: cannot create directory `test': Read-only file system**[/INDENT]

Thanks!

---

### Post by dabl on 2007-09-30
Maybe this will give you an idea or two:

[http://kubuntuforums.net/forums/index.php?topic=3084679.0](http://kubuntuforums.net/forums/index.php?topic=3084679.0)

:)

---

### Post by damijim on 2007-10-03
That worked. Thanks! :)

---

