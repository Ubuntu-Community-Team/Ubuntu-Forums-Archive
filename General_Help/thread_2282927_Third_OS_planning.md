---
title: "Third OS planning"
date: 2015-06-17
forum: General Help
---

### Post by ibates on 2015-06-17
I currently run Ubuntu 14.X on its own HDD on a desktop PC.  There is also another bootable HDD with Windows XP Pro installed and also bootable via a GRUB menu.  This system works perfectly.

But now I have a need to run Windows 8.1 due to applications which require that OS.

I would like to simply install yet another HDD with bootable Windows 8.1 on it, also with the option of choosing that OS at bootup via the GRUB menu.  Ubuntu is still my primary OS with limited access only required  to the other OS, but both Win HDD requiring fairly large databases.

Can I simply install the third HDD (provision does exist in the PC) and then rerun the GRUB update, or are there other steps I should take?  Is it even possible for GRUB to "access" three separate bootable HDD?

I would appreciate advice as to the simplest way to do this.

---

### Post by oldfred on 2015-06-17
Separate hard drive is probably the best choice.

Since it seems to be an older computer you have to install in BIOS boot mode with MBR(msdos) partitions. But you still have to turn off Windows 8's fast startup or else you will have major issues.

You also must make sure Windows hard drive is set as boot drive in BIOS before install or just have that one drive connected when installing. Booting into Ubuntu and running grub's update will then find the Windows to boot as long as it is not hibernated which fast startup is - always hibernated.

---

