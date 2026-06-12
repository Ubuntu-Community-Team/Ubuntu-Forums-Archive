---
title: "External USB Drives, NO GRUB"
date: 2008-06-01
forum: General Help
---

### Post by zpro on 2008-06-01
Well, he something new, running 8.04, ubuntu.
Have two internal hard drives, first drive with Vista, second drive,
with Ubuntu, Grub working okay, can select between Ubuntu (default) or Vista.

NOW, plugin 3 external usb drives (2) formated with NTFS, and 1 with vfat

Reboot: NO GRUB MENU
SHUT DOWN: and Unplug all usb drives
Re-start: Grub Menu okay, and replug in all usb drives, all okay and working,
just fine.

17 times I try this test, and there is Something Wrong with the Grub Menu
where as the usb drives are causing havoc with grub menu or something no reading the startup menu. 
But every time had to unplug the drives, and restart the computer

So, can anyone tell what going on? or what should I look at
PS: all the external drives, are brand new a couple weeks old,
and work fine under 7.10 with rebooting.

Thanks!
:-k

---

### Post by rich86 on 2008-06-01
Are you sure that your bios is trying to boot from the internal drive. It is probably trying to boot from USB but not finding anything (or possibly finding something but stalling).
If you have the option to select boot device at boot hit that key and just choose the internal drive. For a more permanent fix go into the bios setup and change the boot order to the internal drive is above any usb devices or de-select an option to try to boot from usb.

---

### Post by zpro on 2008-06-01
> **rich86 said:**
> Are you sure that your bios is trying to boot from the internal drive. It is probably trying to boot from USB but not finding anything (or possibly finding something but stalling).
If you have the option to select boot device at boot hit that key and just choose the internal drive. For a more permanent fix go into the bios setup and change the boot order to the internal drive is above any usb devices or de-select an option to try to boot from usb.

Thanks For the Tip
What I found was, the Floppy Group Boot Priority -
contain Segate FreeAgent, which was pointing to the seagate external usb drives., SO I made Floppy Boot Last. ( will go back to clear out the data )

Thank You

:)

---

