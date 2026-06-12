---
title: "Why can't i write to my own disk?"
date: 2007-08-28
forum: General Help
---

### Post by icehammer on 2007-08-28
I have 2 partitions - Ubuntu Feisty being installed on the first one..

Everytime i try copying something to the other partitiion, it refuses, saying that i dont have permissions to write to it.. I'm forced to use the terminal for copying, renaming files, etc..
PS: Both the partitions are ext3.

Not that i'm against using the terminal, but i think it'd be easier if i could do the basic stuff with the mouse atleast..

Thanks..

---

### Post by merlinus on 2007-08-28
Post results of:

```

cat /etc/fstab
sudo fdisk -l
mount

```-merlin

---

### Post by bodhi.zazen on 2007-08-28
Try : ```
sudo chown user.groups /mount/point
chmod 770 /mount/point
```

were /mount/point is where the second partition is mounted (/mdeia/???)

If you have files on the partition you may need to use the -R flag

sudo chown -R /mount/point

---

### Post by icehammer on 2007-08-29
/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8f2c0593-a201-464d-b57b-c48b8724a0bd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=8fbb06bd-375a-4533-a21c-5d4cc5a2b4ba /media/hda2     ext3    defaults        0       2
# /dev/hda3
UUID=76f94882-ea02-4170-88bd-31375a446f8f none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

sudo fdisk -l:
```

Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1044     8385898+  83  Linux
/dev/hda2            1045        2237     9582772+  83  Linux
/dev/hda3            2238        2498     2096482+  82  Linux swap / Solaris

```


mount:
```
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
/dev/hda2 on /media/hda2 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
```

---

### Post by icehammer on 2007-08-29
It works now..
Thanks bodhi..!!

---

