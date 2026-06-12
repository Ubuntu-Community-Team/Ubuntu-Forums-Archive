---
title: "After converting ntfs-&gt;fat32, partition not recognized"
date: 2007-03-31
forum: General Help
---

### Post by w1llywonka on 2007-03-31
I have a partition with just files, i.e. not windows or programs, and I converted it with Partition Magic from NTFS to Fat32 so that I could read/write to it in both Windows and Ubuntu.  I believe the partition was recognized previously but now it is not. 

What would be the steps to make it recognizable again?  Think it used to be /dev/sda5.

---

### Post by Obor on 2007-03-31
find out your partition table
```
sudo fdisk -l
```
I'll assume that the new fat32 partition is in /dev/sda5

backup your fstab
```
sudo cp /etc/fstab /etc/fstab_backup
```
open it
```
gksudo gedit /etc/fstab
```

find the line that mentions your /dev/sda5 (or whatever is your new fat partition) and change the line from something like this
/dev/sda5    /media/windows ntfs  nls=utf8,umask=0222 0    0

to something like this
```

/dev/sda5    /media/windows vfat  iocharset=utf8,umask=000  0    0
```
Where /dev/sda5 is your partition and /media/windows is a mount folder. You can change the mount point. just create the folder first i.e. ```
sudo mkdir /media/whatever
```

Now remount fstab
```
sudo mount -a
```

If you get lost just post output of 
sudo fdisk -l
and
 gedit /etc/fstab

---

### Post by Ramses de Norre on 2007-03-31
Have you changed the filesystem type in /etc/fstab?
Edit that file, look for the line for the partition and change "ntfs" to "vfat" and set the options (fourth column) to these: "defaults,auto,utf8,umask=0000,gid=46".

---

### Post by w1llywonka on 2007-04-01
I got it to work with your advice but I took some liberties.  There was an UUID part of fstab file which I deleted and replaced with dev/sda5.  As without deleting it everytime I tried to remount I simply got a message that said 'UUID=### not found.'  This is not going to cause any problems right?

Anyway, many thanks! 

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=e24b25be-925d-456a-a247-21903dfdecf1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=303CBDA83CBD698C /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=C4F05161F0515B2E /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
/dev/sda5 /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=45FB-AEE5  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=87d5b9c3-0871-4827-b494-95931a10fd69 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

