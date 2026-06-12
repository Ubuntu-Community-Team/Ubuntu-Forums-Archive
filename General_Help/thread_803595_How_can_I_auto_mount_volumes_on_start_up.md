---
title: "How can I auto mount volumes on start up?"
date: 2008-05-22
forum: General Help
---

### Post by Neoeyal on 2008-05-22
Hi,
When I mount a volume it will disappear on start up and I'll have to mount again, how do I make it mount **a certain** volume on start up, automatically?

Thanks,
Eyal

---

### Post by bobblehat on 2008-05-22
You can add a line into /etc/fstab to do this. There's a starter here -> [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Neoeyal on 2008-05-22
Thank you
I don't understand what exactly to write there, can you please help me with that?

---

### Post by sisco311 on 2008-05-22
If you mount the partition from the command line, then post the mount command you use. If not post the output of:
```
mount
``````
sudo fdisk -l
``````
cat /etc/fstab
```

---

### Post by Neoeyal on 2008-05-22
> ```
mount
```
```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eyal/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eyal)
/dev/sda1 on /media/Windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
```

> ```
sudo fdisk -l
```
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a600a5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14756   118527538+   7  HPFS/NTFS
/dev/sda2           14757       15217     3702982+   7  HPFS/NTFS
/dev/sda3           15218       30401   121965480    5  Extended
/dev/sda5           15218       29779   116969233+  83  Linux
/dev/sda6           29780       30401     4996183+  82  Linux swap / Solaris

```

> ```
cat /etc/fstab
```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c947aafa-7c66-49e6-b435-8a2040ebdf11 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b86d5d0b-a0d8-4efa-ab4a-6bf0123b7cfc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```


I want to auto mount the HD that is called "Windows"

---

### Post by sisco311 on 2008-05-22
Add this line to the end of the fstab:
> /dev/sda1 /media/Windows ntfs defaults,umask=007,gid=46 0 1

Unmount the partition and create a /media/Windows directory:
```
sudo umount /dev/sda1
sudo mkdir /media/Windows
```
Mount the partition:
```
sudo mount -a
```

To edit the file:
```
gksu gedit /etc/fstab
```

---

### Post by Neoeyal on 2008-05-23
It works thank you!

---

