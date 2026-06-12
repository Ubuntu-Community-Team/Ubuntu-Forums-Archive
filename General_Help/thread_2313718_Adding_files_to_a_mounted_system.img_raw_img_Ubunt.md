---
title: "Adding files to a mounted system.img raw img Ubuntu"
date: 2016-02-15
forum: General Help
---

### Post by james200 on 2016-02-15
Hi All,

Have successfully used all the tools and guide here ([http://forum.xda-developers.com/showthread.php?t=2600364](http://forum.xda-developers.com/showthread.php?t=2600364)) to mount an RAW EXT4 .img from Android.

However, while I have managed to get read/write access to the mounted raw partition (i.e. I can delete files) everytime I try to add a file (no matter how small) it claims there is no space available.

Thinking this is a permission issue - any ideas?  As far as I know I have full permissions.

Process I've used to get permissions is to mount using instructions in the terminal

simg2img system.img system.raw.img
mkdir system_mnt
mount -t ext4 -o loop system.raw.img system_mnt

(above as per the thread instructions).
then had to use sudo su to get chown on the mount point to add my user and group to the /system_mnt/ and also any specific folders underneath.

Help appreciated (nb - have tried to search for answers without success)

---

### Post by SeijiSensei on 2016-02-15
I believe the mounted image has a fixed size identical to the size of the image on the disk.  You can try copying all the files to another location on your system, manipulating that, then building a new image.  The easiest method to copy the entire disk is to use rsync:
```

cd ~
mkdir linux_image
rsync -av /path/to/system_image/ linux_image/

```

---

