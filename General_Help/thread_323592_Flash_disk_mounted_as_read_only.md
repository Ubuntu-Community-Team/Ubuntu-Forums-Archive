---
title: "Flash disk mounted as read only"
date: 2006-12-22
forum: General Help
---

### Post by kdavies on 2006-12-22
Hi

I have a generic 4gb flash mp3 player.

The device mounts as /media/usbdisk, but only for reading.

This could be a default as there is no vendor name.
The output from cat /proc/mounts is
/dev/sdb1 /media/usbdisk vfat ro,nodiratime,nosuid,nodev,uid=1000,gid=100,fmask=0077,
dmask=0077,codepage=cp437,iocharset=utf8,shortname=mixed,quiet 0 0

Does any one know where to change the settings for pmount or how to make this r/w

Ta

Kevin

---

### Post by aysiu on 2006-12-22
Can you plug it in and post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

