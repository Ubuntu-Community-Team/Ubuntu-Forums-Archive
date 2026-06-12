---
title: "Automount 2st hard drive"
date: 2008-05-18
forum: General Help
---

### Post by UK-Wobbie on 2008-05-18
How can i Automount my 2st hard drive?
When i click on the save mount settings, It do not save the settings when i reboot the computer.

I had a go doing it like this!
/dev/disk       /media/disk  ext3   defaults   0   1

But it did not work.:confused:


Thanks

---

### Post by TeoBigusGeekus on 2008-05-18
Post us the output of
```
sudo fdisk -l
```
(-L)
and
```
mount
```
as well as the contents of your fstab file
```
gksudo gedit /etc/fstab
```

---

### Post by UK-Wobbie on 2008-05-18
> **TeoBigusGeekus said:**
> Post us the output of
```
sudo fdisk -l
```
(-L)
and
```
mount
```
as well as the contents of your fstab file
```
gksudo gedit /etc/fstab
```


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f85a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19270   154786243+  83  Linux
/dev/sda2           19271       19457     1502077+   5  Extended
/dev/sda5           19271       19457     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e78b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Disk /dev/sdc: 1047 MB, 1047265280 bytes
64 heads, 32 sectors/track, 998 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xa20496b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         998     1021935+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(996, 63, 32) logical=(997, 63, 31)

```



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d0af235f-11e9-4a8e-8919-0be0a8f6370f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5a8047b8-2664-4153-a942-e7ec93d1a38f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I did have one line what use to work in 7.10 for making my 2st drive to automount but it will not work in 8.04

/dev/hdd1   /media/hdd1   ext3   defaults   0   1

---

### Post by TeoBigusGeekus on 2008-05-18
Which is the drive you want to mount?
Also which is its mount point?
Post the output of
```
mount
```

---

### Post by ibuclaw on 2008-05-18
Don't you mean 2nd hard drive?
Put the following into your fstab file:
```
/dev/sdb1 /media/sdb1 ext3 defaults 0 1
```
Save, quit, and type in the terminal "**sudo mount -a**"

Regards
Iain

---

### Post by UK-Wobbie on 2008-05-18
> **TeoBigusGeekus said:**
> Which is the drive you want to mount?
Also which is its mount point?
Post the output of
```
mount
```

I do not know what one, When i do mount it! 
It says 
/media/disk

But when i mount a USB pen drive it says the same thing

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

```

---

### Post by TeoBigusGeekus on 2008-05-18
```
gksudo gedit /etc/fstab
```
Add this line at the end
```
/dev/sdb1     /media/disk     ext3     relatime     0     2
```
Save, reboot and post us what happened.

---

### Post by UK-Wobbie on 2008-05-18
> **TeoBigusGeekus said:**
> ```
gksudo gedit /etc/fstab
```
Add this line at the end
```
/dev/sdb1     /media/disk     ext3     relatime     0     2
```
Save, reboot and post us what happened.

It worked!
Thank you for your help :mrgreen:

Robbie

---

