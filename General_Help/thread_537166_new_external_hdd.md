---
title: "new external hdd"
date: 2007-08-28
forum: General Help
---

### Post by krelverehan on 2007-08-28
I just got a hold of this brand new 160gb external hdd (using usb 2.0) I've got it in a bt-380 series bytecc case (the cheapest one) which uses remote power to operate. Now I've put it all together and I cant seem to get my system to recognize it (I use edgy elf). I spent a little time seeing if there was another forum on installing new external hdd's but I can't seem to find one. Any ideas on how to get it to work?

---

### Post by krelverehan on 2007-08-28
Here is a bit more information to narrow down the problem:

I can hear the external hdd working when it is plugged in and all the lights light up.
I know that the usb port it is plugged into works.
My knowledge of if it is recognizing it or not consists of my checking the /media folder.

---

### Post by merlinus on 2007-08-28
With the drive plugged it, post results of:

```

sudo fdisk -l
mount
cat /etc/fstab

```

-merlin

---

### Post by krelverehan on 2007-08-28
```

krel@Namcle:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19080   153260068+  83  Linux
/dev/hda2           19081       19457     3028252+   5  Extended
/dev/hda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
16 heads, 63 sectors/track, 77557 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1985     1000408+  82  Linux swap / Solaris
/dev/hdb2            1986       77557    38088288   83  Linux

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

``````

krel@Namcle:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-12-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

``````

krel@Namcle:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1a424643-1968-4d48-9124-aa0efff63329 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=05fafb15-50eb-41cc-a7c6-308047528e3a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

Thanks!

---

### Post by merlinus on 2007-08-28
Is the partition hdb2?

Have you ticked the appropirate boxes in System/Preferences/Removable Drives and Media?

Have you created a mountpoint for the partition?  Have you tried to manually mount it?

-merlin

---

### Post by krelverehan on 2007-08-28
a) I am not sure, it is a brand new hdd if that means anything.
b) I have ticked the appropriate boxes.
c) I am not sure how to do this and any instruction would be greatly appreciated.

-Krel

---

### Post by merlinus on 2007-08-28
Have you formatted it?

I am trying to figure out if ubuntu lists it as hdb2 or sda, neither of which are mounted.

According to sudo fdisk -l, hdb2 is formatted as ext3, and sda is not formatted at all.

-merlin

---

### Post by krelverehan on 2007-08-28
No, I have done nothing with it thus far. How do you go about formatting a new hdd?

---

### Post by merlinus on 2007-08-28
Try this:

```

sudo fdisk /dev/sda

```If that is successful, then

```

mkfs -t ext3 /sda1

```

-merlin

---

### Post by merlinus on 2007-08-28
Better yet, try this:

```

sudo mkfs.ext3 /dev/sda1

```-merlin

---

### Post by krelverehan on 2007-08-28
Success! Thanks for all the help. It is all up and running and my knowledge of file systems is substantially larger.

-Krel

---

### Post by merlinus on 2007-08-28
You are most welcome.  Glad it worked!

BTW, which of the formatting commands worked for you?

-merlin

---

