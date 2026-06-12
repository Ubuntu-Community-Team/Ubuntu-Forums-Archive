---
title: "How to automount NTFS usb sticks?"
date: 2012-12-05
forum: General Help
---

### Post by netimen on 2012-12-05
Hi all, I'm running the Xubuntu 12.10 on a Lenovo T520 laptop.

If I plug a FAT formatted usb stick, it's mounted automatically, but if I plug in a NTFS formatted one, I have to mount it manually.

How to make NTFS usb sticks to mount automatically when plugged?

My /etc/fstab in case it helps:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=cd221c3e-44a8-459e-9dfb-04787f1cd0b6 none            swap    sw              0       0

```

---

