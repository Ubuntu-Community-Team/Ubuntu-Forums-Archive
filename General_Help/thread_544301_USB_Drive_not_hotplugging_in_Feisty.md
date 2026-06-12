---
title: "USB Drive not hotplugging in Feisty"
date: 2007-09-06
forum: General Help
---

### Post by lincolnlad on 2007-09-06
Hello,

I have a new install of 7.0.4 and at boot up my USB drive (ext3 and VFAT partitions) is being recognised and mounted read only.  However, if I plug it in after boot up, gnome volume manager doesn't do anything with it and it remains unmounted.  I've set gnome volume manager to auto mount hot plugged drives.


Can anyone explain to me why it's mounting the drive read only at boot and not at all if plugged in later?

Thanks very much

---

### Post by lincolnlad on 2007-09-08
FIXED:

I have a Seagate FreeAgent 320GB drive.  I reformatted the drive and checked for no errors on the disk.  When I plug it in, gnome volume manager automounts the drive.  I have to unmount the drive before unplugging it or else I get the warning messages about not removing the drive safely.  After correctly unmouning the drive, I have to **remove the power source from the back of the drive, plug the power source back in and then plug the USB cable into my PC.**  If I don't remove the power cable from the drive, Ubuntu/Gnome, does not automount the drive.

It's not 100% hot plugging, but it works.  I wonder if it's got anything to do with the power management of this particular hard drive.

---

### Post by zekica on 2007-09-08
> It's not 100% hot plugging, but it works. I wonder if it's got anything to do with the power management of this particular hard drive.

I think it has something to do with Linux. It doesn't cut the power to USB devices when you umount them.

---

