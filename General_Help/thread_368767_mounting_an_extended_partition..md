---
title: "mounting an extended partition."
date: 2007-02-23
forum: General Help
---

### Post by geck07 on 2007-02-23
i want to mount an extended partition of 183 gbs.it consists of three fat32 partitions.i tried to add lines in my fstab file.output of my fdisk -l command is:

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2354    18908473+   7  HPFS/NTFS
/dev/hdc2           26475       30401    31543627+  83  Linux
/dev/hdc3           26346       26474     1036192+  82  Linux swap / Solaris
/dev/hdc4            2355       26345   192707707+   5  Extended
/dev/hdc5            2355        8847    52154991    b  W95 FAT32
/dev/hdc6           19684       26345    53512483+   b  W95 FAT32
/dev/hdc7            8848       19682    87032106    b  W95 FAT32


plz help me mount it.......


my fstab file looks like:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               reiserfs notail          0       1
/dev/hdc1       /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc4       /media/hdc4     ext3    defaults,nls=utf8,umask=007,gid=46 0       1




regards

---

### Post by taurus on 2007-02-23
Edit /etc/fstab and remove the last line, /dev/hda4, from it since it's an extended partition.  Then, add these three lines to the end of it.

```

/dev/hdc5   /media/hdc5   vfat   iocharset=utf8,umask=000   0   0
/dev/hdc6   /media/hdc6   vfat   iocharset=utf8,umask=000   0   0
/dev/hdc7   /media/hdc7   vfat   iocharset=utf8,umask=000   0   0

```
Save it.  Now, create three new mount points and mount them.

```
sudo mkdir /media/hdc5 /media/hdc6 /media/hdc7
sudo mount -a
df -h
```

---

