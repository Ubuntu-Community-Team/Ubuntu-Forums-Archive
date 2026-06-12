---
title: "completely remove windows"
date: 2006-11-14
forum: General Help
---

### Post by Slothman on 2006-11-14
Hi,

I want to completely uninstall windows, so I downloaded Gparted to delete the windows partition and resize linux to take all the space.... But the windows ntfs partition says "boot" in the flag section in Gparted. Will this remove my boot loader if I delete the windows partition??

cheers

---

### Post by aysiu on 2006-11-14
Did you install Grub to the MBR when you installed Ubuntu? Or did you manually edit the Windows boot.ini file and *dd* copy Grub to be available for the Windows boot loader?

If you have no idea what I'm talking about, you probably installed Grub to the MBR, in which case, it's perfectly fine to delete the Windows partition.

---

### Post by MWAAAHAAA on 2006-11-14
No, the boot flag is just a bit that is set in the partition table. DOS required this flag to be able to boot. HOWEVER, you should make sure that you are using GRUB (or LILO) as your boot loader as the one shipped with Windows will complain that it isn't able to find Windows anymore.

---

