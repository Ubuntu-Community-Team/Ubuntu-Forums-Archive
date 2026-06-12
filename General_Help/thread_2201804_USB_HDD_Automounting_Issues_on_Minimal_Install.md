---
title: "USB HDD Automounting Issues on Minimal Install"
date: 2014-01-26
forum: General Help
---

### Post by gatorstudent20 on 2014-01-26
Hi All,

I just set up an Intel NUC (D34010WYK) with an Ubuntu Minimal install.  I've also installed and set up xbmc.  Everything is working great (after some initial UEFI boot issues which was corrected with a grub rescue disk).

The only thing I can't get up and going is the auto-mounting of my USB hard-disk.  Any help would be much appreciated.  Here are my notes:
- I've set up the drive to mount in /etc/fstab as follows
```
UUID=4FE8-C1C0 /media/HDTB vfat defaults,errors=continue,noauto,rw,umask=000 0 0
```

- I've added a mount command to /etc/rc.local
```
sudo mount -a
```

- I've installed usbmount and udev. At first I tried without these, then added them since they helped automount once the USB drive is detected.

- When I say that the drive is undetected, I mean that it is not seen or detected in blkid, df, or lsusb.

- If I reboot the device, the drive is not detected.  If I unplug the device and then plug it back in, it becomes visible (and usbmount automounts it according to fstab). If I reboot the device, the drive is not detected and I need to unplug and plug it back in again.

Any advice to get this working is much appreciated!
Thanks

---

### Post by gatorstudent20 on 2014-02-02
Bump
Just in case anyone has any suggestions.  Thanks!

---

