---
title: "Splash (partially) gone after screwing with partitions?"
date: 2008-06-28
forum: General Help
---

### Post by Excalibre on 2008-06-28
I'm running Hardy 64-bit and I just changed my partition table around quite a bit because it was arranged kinda screwily and I want to try out some other distros. Anyhow, I used gparted off the Ubuntu Live CD to do it, and everything went smoothly (in fact, I didn't even need to reinstall GRUB, or change /boot/grub/menu.lst or /etc/fstab as I had expected; although the partitions are in a different order, the device names are the same).

But now when I boot, the splash screen displays for a period of time (the bit when the indicator is just quickly moving back and forth) but then disappears and I see the boot stuff going on (during the part when the splash screen should show an actual progress bar). I checked, and "quiet" and "splash" are still there in /boot/grub/menu.lst.

Also, I'm wondering how Linux determines device names for partitions. My current Hardy partition, for instance, is the last one inside an extended partition, and I created several new partitions to its left, but it's still /dev/sda5, and the newest partition I created inside that extended partition is /dev/sda8, even though it's first on the disk. The same thing is true of my primary partition numbers. So if I install another distro or two, will they agree with Ubuntu on the device names for all these partitions (8 altogether)?

---

