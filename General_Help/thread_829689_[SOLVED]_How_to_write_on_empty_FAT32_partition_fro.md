---
title: "[SOLVED] How to write on empty FAT32 partition from Xubuntu EXT3?"
date: 2008-06-15
forum: General Help
---

### Post by Julita on 2008-06-15
I'm not sure whether I have asked correctly... I have a disc with two partitions. One is FAT32 (empty), the other is EXT3 (Xubuntu 8.04) The point is that I have created FAT32 partition to save there movies, music etc to share, but, when I load Xubuntu, it's not on the Desktop.

---

### Post by Rocket2DMn on 2008-06-15
Can you please post the output of the following commands:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by antmenj on 2008-06-15
I can write and read to my vi$ta partition form ubuntu by going to:

Places ---> Home Folder and looking down the left panel for the right partition and then entering a password to allow access.  I presume this would also work for Fat32.

---

### Post by Julita on 2008-06-15
```
sudo fdisk -l
```
/dev/sda1   *           1        1125     9036531    c  W95 FAT32 (LBA) (it is there...)

```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=009842fd-47a6-4081-b7bf-f863398c81fd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b212c833-2247-4666-8781-93015adaecd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Can't see it here... What would that mean?...

```
sudo blkid
```

/dev/sda1: UUID="0949-97F4" TYPE="vfat" 
/dev/sda5: TYPE="swap" UUID="909a15b2-e4c1-480b-9b25-1e70129ab7b0" 
/dev/sda6: UUID="009842fd-47a6-4081-b7bf-f863398c81fd" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="b212c833-2247-4666-8781-93015adaecd9" 

Here it is...

```
mount
```

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by Julita on 2008-06-15
antmenj, I can't find FAT32 anywhere...

---

### Post by Julita on 2008-06-15
I know I have to mount FAT32, but I have no idea how to do it, if to take into consideration the fact that there is no mounting point, and in fstab the partition is not listed at all... Please, guys, help me...

---

### Post by Julita on 2008-06-15
OK, I have

```
$mkdir /mnt/vfat
``` and edited my fstab.
Now 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=009842fd-47a6-4081-b7bf-f863398c81fd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b212c833-2247-4666-8781-93015adaecd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /mnt/vfat        vfat       users,owner,rw,umask=000 0 0         1   0

---

### Post by Rocket2DMn on 2008-06-15
> **Julita said:**
> OK, I have

```
$mkdir /mnt/vfat
``` and edited my fstab.
Now 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=009842fd-47a6-4081-b7bf-f863398c81fd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b212c833-2247-4666-8781-93015adaecd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /mnt/vfat        vfat       users,owner,rw,umask=000 0 0         1   0

There is too much in your last line, it should probably look like this:
```
/dev/sda1       /mnt/vfat        vfat       users,rw,uid=1000,gid=100,umask=000 0 0
```
Then unmount and remount
```
sudo umount /dev/sda1
sudo mount -a
```

---

### Post by Julita on 2008-06-15
Rocket2DMn, thank you very much!!! Now everything is OK!

---

