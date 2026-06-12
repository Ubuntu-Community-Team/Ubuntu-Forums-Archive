---
title: "Making My Windows Partition Readable By All Users"
date: 2007-12-01
forum: General Help
---

### Post by jlacroix on 2007-12-01
Hello everyone! For some reason, I can't view my Windows partition in KDE. I'm assuming it's a permissions issue. Here is my fstab, how do I mount my Windows partition so everyone can view it?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c6887e16-1f2c-4ec8-976a-87557b0f2a45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=f39f9fad-e29d-42b1-ba84-43e6038983ab none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


```

---

### Post by jlacroix on 2007-12-06
Anyone?

---

### Post by barney_1 on 2007-12-06
I don't see your windows partition anywhere in your fstab.  Here's what I see:

/dev/sdb1 (root partition)
/dev/sdb5 (swap partition)
/dev/hdc (an optical drive)
/dev/hdd (another optical drive)
/dev/fd0 (a floppy drive)

What is the output of:
```
mount -l
```

A guide for mounting windows partitions can be found here:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by jlacroix on 2007-12-06
Here you go.

```
jeremy@jeremy-desktop:~$ mount -l
/dev/sdb1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

---

### Post by taurus on 2007-12-06
Post

```
sudo fdisk -l
```

---

### Post by jlacroix on 2007-12-06
Here you go.

```

jeremy@jeremy-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d8d9c8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38161   306528201   83  Linux
/dev/sdb2           38162       38913     6040440    5  Extended
/dev/sdb5           38162       38913     6040408+  82  Linux swap / Solaris

```

---

### Post by taurus on 2007-12-06
Edit /etc/fstab

```
kdesu kwrite /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```
Save it.  Then, install ntfs-3g driver and create that new mount point and mount it.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1
sudo mount -a
df -h
```
You should see your /dev/sda1 mounted to /media/sda1 from the last output.

---

### Post by jlacroix on 2007-12-06
Bingo!

Thank you!

---

