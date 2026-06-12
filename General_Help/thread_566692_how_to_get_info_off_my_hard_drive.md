---
title: "how to get info off my hard drive????"
date: 2007-10-03
forum: General Help
---

### Post by whos2know on 2007-10-03
Hi,

I have two hard drives.  My first hard drive had Linux Ubuntu on it but I messed up the settings on it and could no longer boot up so, I took my other hard drive that I wasn't using and just put Ubuntu back on it.  My question is how do I get my info off my first hard drive.  The only thing that comes up when I plug it in is two folders (grub and lost and found) and a few other files.... Any help would be great thanks!!!

Bobby

---

### Post by bodhi.zazen on 2007-10-03
You can ```
gksu nautilus /mount/point_of_old_drive
```

If the drive seems blank, what did you do exactly ?

---

### Post by Trab on 2007-10-03
did you have your /home directory as a seperate partition?

make sure both hard-drives are plugged in, and type 
```

sudo fdisk -l

```

copy and paste that info here.


if it was not a seperate partion, mount the hard drive, type
```

cd /
ls

```

and copy and paste that.

---

### Post by whos2know on 2007-10-03
hi, 

here is the info

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9402    75521533+  83  Linux
/dev/hda2            9403        9729     2626627+   5  Extended
/dev/hda5            9403        9729     2626596   82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        4864    38821072+   5  Extended
/dev/sda5              32        4864    38821041   8e  Linux LVM


Thank you for the help!! :)

Bobby

---

### Post by whos2know on 2007-10-05
anyone help? please?  thank you!!

---

### Post by thirddeep on 2007-10-05
Type in 
```
mount
```
and paste it here.  Then we can see if HDA or SDA is your current drive and help further.

---

### Post by whos2know on 2007-10-05
here is the info...

```
bobby@Ubuntu-Laptop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-12-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev)

```

Thank you again!!

---

### Post by thirddeep on 2007-10-05
OK

HDA is your current working drive.
SDA is your old drive.

As you can see at the bottom, ubuntu has already mounted it on /media/disk

If you browse to /media/disk, you should find your data there.

Thd.

---

### Post by whos2know on 2007-10-06
yes, ubuntu did mount it but I can only access one part of the partition.  How do I access the rest of it??

---

### Post by fwhr on 2007-10-10
whos2know, use this:
sudo cryptsetup --help
after reading (or googling) mount your encrypted volume and get the data.

---

