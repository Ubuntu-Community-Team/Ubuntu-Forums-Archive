---
title: "how to display disk label for usb device?"
date: 2007-01-10
forum: General Help
---

### Post by joey_joe_joe on 2007-01-10
within gnome or kde, hal mounts my usb disks, retrieving the volume label, for example myiPod, and creating an nice mountpoint like /media/myiPod.
However, when using other window manager, or no window manager at all, the usb device is not mounted. I've made a rule in /etc/udev/rules.d to execute a script when i add a usb device, however instead of just mounting the device to /media/sdb1, i would like to retrieve the disk label and mount the device to /media/<disklabel>

I know you can use mtools for vfat partitions, e2fsprogs for ext2/3 partitions to retrieve disk label, but this is a somewhat over complex method since i must install package for each partition type. is there any tool preinstalled that can retrieve disk labels. How does hal retrieve disk label when my flash drives are mounted in gnome?

any help much appreciated.

---

### Post by bodhi.zazen on 2007-01-10
Plug in your device(s)

In a terminal:```
ls /dev/disk/by-label -l
```

---

### Post by joey_joe_joe on 2007-01-10
thanks, this is a perfect solution!

---

