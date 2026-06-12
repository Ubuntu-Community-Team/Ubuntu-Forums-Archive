---
title: "SD Card Not Copying Or Formating"
date: 2014-09-13
forum: General Help
---

### Post by minecraftpe-al on 2014-09-13
So when I go to copy music to my SD card it will not let me. I looked it up on-line all websites said format the SD card but when i go to do that I get this message
```
Error mounting /dev/mmcblk0p1 at /media/mrinterbugs/4877-16FC: Command-line `mount -t "vfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush" "/dev/mmcblk0p1" "/media/mrinterbugs/4877-16FC"' exited with non-zero exit status 32: mount: /dev/mmcblk0p1: can't read superblock
```

---

### Post by gordintoronto on 2014-09-14
How are you trying to format the SD card? I would use this command: sudo gparted

People might be able to give you better help if you mentioned what version of Ubuntu you are using.

---

### Post by redrumrogue on 2014-09-14
I'd try gparted as well.  If that doesn't work I'd try wiping the first few MB of the card with zeros to blow away the partition table and any possible corruption and then use gnome-disks or gparted to format the device.  To wipe the device type the following into a terminal window  ...

sudo dd if=/dev/zero of=/dev/XXX bs=1M count=1024

This would overwrite the first 1GB (1MB x 1024) which should do the job.  IMPORTANT!!!! - make absolutely sure you set your "of=/dev/XXX" bit to the correct device!  If you're unsure then ask here.

---

### Post by minecraftpe-al on 2014-09-14
Ok I already use gpated and all my devices are read only plz help. I know the bug but i can not find a fix as this command does not work  [COLOR=#000000][FONT=Ubuntu Mono]sudo nautilus now all i want to do is copy to the usb or sd card[/FONT][/COLOR]

---

