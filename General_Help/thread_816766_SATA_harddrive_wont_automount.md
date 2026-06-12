---
title: "SATA harddrive wont automount"
date: 2008-06-03
forum: General Help
---

### Post by miickEe on 2008-06-03
Hey

I have a 500GB SATA harddrive that won't automount. It will mount only if I go to Places -> Computer and then double click on it. I'd like to be able to have it mount like the other drives automatically when the system boots up.

How would I go about this?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=05a3d8a2-edad-4422-a692-7007b8f5b479 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=4829-6CBE  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=ab443c80-548b-48a3-9111-69eaa9f0d974 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

When I type the mount command:
```

miickee@miickee-gutsy:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb2 on /media/MIICKEE'S I type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/hdc on /media/cdrom0 type udf (ro,nosuid,nodev,user=miickee)
**/dev/sda1 on /media/Music type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)**

```

/dev/sda1 is the name of the harddrive in question.

Thanks in advance

miickee

---

### Post by miickEe on 2008-06-03
I tried to add this line to the fstab. Needless to say it made me think I wiped everything off the drive. It's all good now that I've rebooted and deleted the line.

```

#/dev/sda1
UUID=E23C9FD13C9F9EDB /dev/sda1 ntfs user,auto 0 0

```

---

### Post by markbusu on 2008-06-03
From the Gnome Panel, click System->Preferences->Removable Drives and Media and then uncheck the first two boxes on the storage tab. This will turn off automounting for everything not defined in /etc/fstab, and you can turn it back on if desired as easily. 

Check if you have modified that option...

---

### Post by miickEe on 2008-06-03
> This will turn off automounting for everything not defined in /etc/fstab, and you can turn it back on if desired as easily. 

Not sure if I worded this correctly. In terms of the answer you've given, you're saying to uncheck the first two in storage to turn off automounting. What I'm looking for is for a specific drive to be automounted as well as those that are already automounted.

The first two options are checked in the Remove Drives and Media

---

