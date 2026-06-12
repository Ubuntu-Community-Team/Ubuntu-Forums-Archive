---
title: "Please help. Hard drive vanished"
date: 2007-06-05
forum: General Help
---

### Post by pacguy on 2007-06-05
After installing ubuntu and then mounting my second hd I was able to access it and copy files from it but couldn't copy files to it. I then used the ntfs config tool in the system file but when I enabled read/write access to the drive it vanished. The fdisk shows that the drive is there along with the partition manager but I can't figure out how to remount it. All I need to do is mount it so I can pull out some files and then I'm going to reformat it. It doesn't need to be writeable, just visible.

---

### Post by daschmidty on 2007-06-05
have you tried mounting it from the terminal?
do
```
sudo mount -t ntfs /dev/(partition) (folder to mount to) 
```

---

### Post by pacguy on 2007-06-05
How should I go about mounting it. Here's my fdisk.

> Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14311   114953076   83  Linux
/dev/hdc2           14312       14593     2265165    5  Extended
/dev/hdc5           14312       14593     2265133+  82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401    7  HPFS/NTFS

Sorry but I'm kinda bad with using terminal.

---

### Post by daschmidty on 2007-06-05
first create a mountpoint for the drive:
```
sudo mkdir /media/windows
```
now mount the partition to that mountpoint
```
sudo mount -t ntfs /dev/hdd1 /media/windows
```
now if you browse to /media/windows you should be able to read the drive NOTE(you may need to run nautilus/konqueror as root to open the folder)

---

### Post by pacguy on 2007-06-05
Awesome. That got it. Thank you so much.

---

### Post by pacguy on 2007-06-05
Wait, nevermind. I can see the files now but I can't copy them from one drive to another. Any idea on how to make that happen.

---

### Post by pacguy on 2007-06-05
Bump bump da bump

---

