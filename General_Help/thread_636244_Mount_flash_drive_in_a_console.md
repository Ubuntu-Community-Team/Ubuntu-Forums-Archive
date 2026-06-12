---
title: "Mount flash drive in a console"
date: 2007-12-09
forum: General Help
---

### Post by runemaste644 on 2007-12-09
Ok, after letting my laptop turned off for a few weeks ive lost nvidia drivers. I need to back some of my data up on a flash drive, but in a console, it doesnt automount and hence isnt visible in /media. How can i mount my flash drive to the usual /media directory from the console? If this helps, /dev/sda is my first hard disk and both disks are vfat.

---

### Post by ajgreeny on 2007-12-09
First make a mount point with ```
mkdir /home/username/flash
```
You can easily find the flash drive device name with  ```
sudo fdisk -l
``` in terminal and then use normal mount commands for a fat32 partition ```
sudo mount /dev/sdxX /home/username/flash/ -t vfat -o iocharset=utf8,umask=000
```to mount it and copy files using the **cp** command.  Should be easy enough.

---

