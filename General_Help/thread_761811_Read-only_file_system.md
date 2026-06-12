---
title: "Read-only file system"
date: 2008-04-21
forum: General Help
---

### Post by estanton on 2008-04-21
Hi there my second hard drive has mysteriously become unresponsive this morning. It's running FAT32 and when I check it's properties it says the owner is root, and the whole thing is now read-only. How can I edit the permissions for this drive to restore it to read/write?

---

### Post by pseudo-random on 2008-04-21
From a terminal:
```
sudo chown (yourname) /media/???
```
With ??? being your HD. Use 'mount' to find out.

example:
```
sudo chown pseudo /media/sda1
```

---

### Post by sisco311 on 2008-04-21
> **pseudo-random said:**
> From a terminal:
```
sudo chown (yourname) /media/???
```With ??? being your HD. Use 'mount' to find out.

example:
```
sudo chown pseudo /media/sda1
```

You can't change the owner of a fat partition with chown.

@estanton

post the output of:
```
mount
```
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

---

### Post by estanton on 2008-04-21
yeah i tried chown but no dice so i came here :)

mount
> /dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type vfat (rw,noexec,nosuid,nodev,fmask=0111,dmask=0000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9a473b9b-8975-47c7-8ed2-d006efd461f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=03f3e917-7dac-46b5-82cf-955d0ae6c3a2 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/hdb1 /media/hdb1 vfat rw,user,fmask=0111,dmask=0000 0 0

and fdisk
> 
Disk /dev/hda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96eb7008

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2382    19133383+  83  Linux
/dev/hda2            2383        2491      875542+   5  Extended
/dev/hda5            2383        2491      875511   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4eb29d36

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001    b  W95 FAT32


The same thing happened with a microSD card (which isn't in the computer at the moment) where it suddenly became read-only.

---

### Post by chrisccoulson on 2008-04-21
This comes up time and time again for some reason. It has most likely gone read-only because there are errors on the filesystem. What you need to do is unmount the volume, then run dosfsck on it to correct the errors.

Assuming the problem partition is /dev/hdb1, try this:
```
sudo umount /dev/hdb1
sudo dosfsck -av /dev/hdb1
```

Note that these symptoms are extremely common after not properly unmounting FAT32 partitions (ie, unplugging an external drive / power failure or other unclean shutdown)

---

### Post by sisco311 on 2008-04-21
deleted

---

### Post by estanton on 2008-04-23
OK the previous commands worked, but it seems every time I reboot it ends up back in the same situation again.

---

