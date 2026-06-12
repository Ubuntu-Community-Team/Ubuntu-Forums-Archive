---
title: "File Permisions won't stick!"
date: 2007-01-18
forum: General Help
---

### Post by Lymen on 2007-01-18
Hi
I got a new hard drive, formatted it fat32, mounted it in my media folder... great!
I used alt F2 and gksudo nautlius, (logged in as root) and right clicked and changed 
permissions in both the /dev folder and the /media folder of my new drive.  I was able 
to copy some files onto the new drive as root, but when I tried to copy more as user 
I got the "You dont have permission" error.  

next I tried to use the command line...  these are the commands I tried.
sudo chmod a+rw /dev/hde1
sudo chmod a+rw /media/bigdrive
sudo chmod 777  /media/bigdrive

I still don't have permission to write as user : (

any tips as to what I am doing wrong would be appreciated!

thanks.

---

### Post by taurus on 2007-01-18
Those three commands won't work for fat32/vfat filesystem.  How did you mount it, from a terminal or with /etc/fstab?

---

### Post by Lymen on 2007-01-18
I checked the storage device manager and I guess I must have formatted in ext3.  
the storage device manager is also how I mounted it.

here is my fstab:
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# /dev/hdb1
UUID=7c944699-b69f-4a92-afe6-4d428bbaff26  /                ext3         defaults,errors=remount-ro  0  1  
# /dev/hdb5
UUID=4c46a843-0eda-49cd-866c-9c83e4eb0d7f  none             swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0    udf,iso9660  user,noauto                 0  0  
/dev/hdd                                   /media/cdrom1    udf,iso9660  user,noauto                 0  0  
/dev/                                      /media/floppy0   auto         rw,user,noauto              0  0  
/dev/hda1                                  /media/hda1      ntfs         nls=utf8,umask=0222         0  0  
/dev/hde1                                  /media/bigdrive  ext3         defaults                    0  0  

thanks for the quick reply!

---

### Post by taurus on 2007-01-18
Are you sure /dev/hde1 is ext3?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Lymen on 2007-01-18
sorry, had to run to work for a while..
fdisk says it is fat32.  heres the output:
user@user-desktop:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7297    58613121    7  HPFS/NTFS

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2392    19213708+  83  Linux
/dev/hdb2            2393        2498      851445    5  Extended
/dev/hdb5            2393        2498      851413+  82  Linux swap / Solaris

Disk /dev/hde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       30401   244196001    b  W95 FAT32
user@user-desktop:~$

---

### Post by taurus on 2007-01-18
/dev/hde1 is fat32/vfat, not ext3.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
/dev/hde1 /media/bigdrive ext3 defaults 0 0 
```
with this line.

```
/dev/hde1   /media/bigdrive   vfat   iocharset=utf8,umask=000   0   0
```
Save it and reboot.

Now, see if you can write to /media/bigdrive.

---

### Post by bodhi.zazen on 2007-01-18
Change

/dev/hde1 /media/bigdrive ext3 defaults 0 0

to

/dev/hde1 /media/bigdrive auto auto,users,umask=000 0 0

```
gksudo gedit /etc/fstab
```

Then:```
sudo umount /media/bigdrive
mount /media/bigdirve

ls -l /media
```

You should have the permissions you want :)

---

### Post by Lymen on 2007-01-18
THANK YOU!!
you all are so incredibly helpful, and quick to respond. thank you, thank you. 
that worked!  I'm off to learn samba.  I'll be back.

---

