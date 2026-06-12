---
title: "[SOLVED] Strange Harddrive Problem"
date: 2008-02-05
forum: General Help
---

### Post by DTPhantom on 2008-02-05
Hey guys, I had to reinstall my XP partition and couldn't manage to reinstall grub so i just ended up reinstalling ubuntu too.  Now my problem is when i restart my computer and boot into ubuntu it won't automount my harddrives like it use to.  Which is a problem because i have my pictures, music, and videos as links to save space(no need to have exact copies for both OS's) but this causes no background to show up untill i mount my XP hard drive.  Does anybody know how i would go about fixing this?

---

### Post by jken146 on 2008-02-06
Please post the outputs of the following commands:

```
sudo fdisk -l
```

```
mount
```

```
cat /etc/fstab
```

---

### Post by DTPhantom on 2008-02-06
here is the first 
> 
Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcd9a955

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        3187    25599546    7  HPFS/NTFS
/dev/hdc2   *        6375       19457   105089197+   7  HPFS/NTFS
/dev/hdc3            3188        6236    24491092+  83  Linux
/dev/hdc4            6237        6374     1108485    5  Extended
/dev/hdc5            6237        6374     1108453+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d411d41

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9cb78923

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS


the second

> 
/dev/hdc3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/hdb on /media/cdrom1 type udf (ro,nosuid,nodev,user=bryan)
/dev/hdd1 on /media/XP type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/250 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


and the third 
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3
UUID=31aab67a-8cfc-4860-a374-6795db4dc405 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=74af9d4d-a842-4213-9711-ce5b8e45a130 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0


---

### Post by osos on 2008-02-06
do you have ntfs -drivers installed?

---

### Post by DTPhantom on 2008-02-06
i assume i do i can read and write to it after i mount it, plus during my previous installations I never had to install something extra it would just auto mount my drives as soon as i booted up.

---

### Post by jken146 on 2008-02-06
All your NTFS drives are missing from /etc/fstab.  Some instructions on adding them in: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If you want the partitions to show up as desktop icons, you should create mount points within the directory /media

---

### Post by DTPhantom on 2008-02-06
thank you but why would it only happen on this install and never on my older ones(a mix of both 7.04 and 7.10 installs)

---

### Post by logos34 on 2008-02-06
yes, and what's strange is that two of the four (sda1 and hdd1) are mounting with ntfs-3g despite not being in fstab (at least one is an internal disk)

---

### Post by DTPhantom on 2008-02-06
> **logos34 said:**
> yes, and what's strange is that two of the four (sda1 and hdd1) are mounting with ntfs-3g despite not being in fstab (at least one is an internal disk)

they're all internal disks.  There is a 120Gb IDE which holds windows XP and most of my documents(music, pictures, videos, things like that), a 250Gb SATA which is just a general back up folder and other stuff i don't put else where, then a 160Gb IDE partitioned into 110 Gb, and 2x25gb one of the 25gb is vista the other is ubuntu.

---

### Post by jken146 on 2008-02-06
I haven't a clue why they aren't auto mounting, but if you put entries in fstab for those partitions they *will* mount at boot.

---

### Post by DTPhantom on 2008-02-06
> **jken146 said:**
> I haven't a clue why they aren't auto mounting, but if you put entries in fstab for those partitions they *will* mount at boot.
ok thanks but i have to admit i'm not quite following along with that quide since apparently they have changed the way fstab looks in newer versions of ubuntu.

on mine
bryan@lexinton:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3
UUID=31aab67a-8cfc-4860-a374-6795db4dc405 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=74af9d4d-a842-4213-9711-ce5b8e45a130 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

i assume i put 
/dev/hdd1    /media/XP 
but i'm not sure what i would put after that.

---

### Post by jken146 on 2008-02-06
/dev/hdd1    /media/XP defaults,umask=007,gid=46 0       1

---

### Post by DTPhantom on 2008-02-06
> **jken146 said:**
> /dev/hdd1    /media/XP defaults,umask=007,gid=46 0       1

Ok I tried that and it didn't work.  Not only didn't it mount the hard drive automatically but when i went to manually mount it, i was told i don't have permission to do that.

---

### Post by logos34 on 2008-02-06
> **DTPhantom said:**
> Ok I tried that and it didn't work.  Not only didn't it mount the hard drive automatically but when i went to manually mount it, i was told i don't have permission to do that.

typo--need a** filesystem** type:

try

> /dev/hdd1 /media/XP [COLOR="Blue"]ntfs[/COLOR] defaults,umask=007,gid=46 0 1

or

> /dev/hdd1 /media/XP [COLOR="Blue"]ntfs[/COLOR] defaults,[COLOR="Blue"]nls=utf8[/COLOR],umask=007,gid=46 0 1

---

### Post by DTPhantom on 2008-02-07
Thank you very much the second one worked.

---

