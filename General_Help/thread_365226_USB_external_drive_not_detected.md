---
title: "USB external drive not detected"
date: 2007-02-19
forum: General Help
---

### Post by illiterate_light on 2007-02-19
I have a fresh install of Dapper 6.06.1, and can't get it to detect an external USB drive (FAT).  The drive is detected automatically if I boot into Ubuntu 5.10 or WinXP on the same machine.  I tried:

> sudo mount -t vfat /dev/sda /mnt/usb

and it tells me:

> mount: special device /dev/sda does not exist

Also tried fdisk -l /dev/sda, which gives no response.

I don't see any signs that the drive is detected in any way.  I have System -> Preferences -> Removable Drives and Media set to automatically detect and mount hot-plugged USB drives.

Any ideas?  Thanks for any help.

---

### Post by taurus on 2007-02-19
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by illiterate_light on 2007-02-19
Magically, it works now... I've been messing with it for three days, and finally I decided to plug it in, unplug it, and then replug it three times quickly, and all of a sudden it's detected, and is now detected and automatically mounted on boot as well.

Yesterday, I ran fdisk -l and it only showed my two internal drives.  Now it shows the external one too.

Thanks for getting back to me.  Everything seems to be working smoothly now, and I'm loving the fresh install of 6.06.1.

---

