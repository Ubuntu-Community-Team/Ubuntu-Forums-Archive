---
title: "Dual Boot, windoze has quit booting"
date: 2007-05-15
forum: General Help
---

### Post by mrehorst on 2007-05-15
I've been running a dual boot AMD-64 Ubuntu and win2k for many months and all has been fine until a week ago when windoze decided to quit working.  It boots OK right to the point where the desktop background shows up, the mouse pointer is dead center on the screen, then the window that says "windows is starting up" is displayed.  From there the HDD light is on and the machine is hung-up and won't do anything.

I've tried booting to safe mode and it doesn't work.  I tried doing a "repair" using the CDROM and it didn't help.  I tried running spinrite on the partitions where win2k is installed and no workee.  

I'd try reinstalling but I'm guessing it will trash Grub and linux.

Anyone with similar experience ever fixed the problem without trashing linux?

Thanks,

MR

---

### Post by dcstar on 2007-05-15
> **mrehorst said:**
> I've been running a dual boot AMD-64 Ubuntu and win2k for many months and all has been fine until a week ago when windoze decided to quit working.  It boots OK right to the point where the desktop background shows up, the mouse pointer is dead center on the screen, then the window that says "windows is starting up" is displayed.  From there the HDD light is on and the machine is hung-up and won't do anything.

I've tried booting to safe mode and it doesn't work.  I tried doing a "repair" using the CDROM and it didn't help.  I tried running spinrite on the partitions where win2k is installed and no workee.  

I'd try reinstalling but I'm guessing it will trash Grub and linux.

Anyone with similar experience ever fixed the problem without trashing linux?

Thanks,

MR

A Windows re-install will just overwrite the boot sector, you can actually save this data and restore it, or simply use the "Re-install Grub" instructions available in this forum.

Just make sure you don't wipe the whole disk on re-install.

---

