---
title: "Unable to access NTFS Windows Partition anymore."
date: 2008-01-21
forum: General Help
---

### Post by Marco Ceppi on 2008-01-21
Hey all,

I've been trolling the forums for a long time - and using Ubuntu even longer. Everything was going just fine until earlier today I installed grub-gfxboot to change the grub selection screen.

That installed fine. However after about 3 reboots I am unable to access the "Windows XP" under other OS's - I am also unable to mount my windows partition.

I had it set up in fstab to mount on startup, but now I can't even manually mount. I get this from console:

> marco@marco-linux-laptop:/dev$ sudo mount -a
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

I've searched around for a bit on both Google and here. Unable to find anyone with a similar problem.


Please someone tell me there is an easy way to fix this.

Marco

---

### Post by Marco Ceppi on 2008-01-29
Solved.

I had to fix using the Windows Recovery Console fixmbr and fixboot method. Then Super Grub Disk to get back into linux.

---

