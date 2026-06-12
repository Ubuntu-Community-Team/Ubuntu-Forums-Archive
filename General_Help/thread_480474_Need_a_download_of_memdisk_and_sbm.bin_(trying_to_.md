---
title: "Need a download of memdisk and sbm.bin (trying to boot CD)"
date: 2007-06-21
forum: General Help
---

### Post by TacticalPenguin on 2007-06-21
I've been using Xubuntu for a while but now I want to change to plain ol' ubuntu, a fresh install, not just installing ubuntu-desktop. But of course grub loads before my laptop boots from CD and when it boots up it says absolutely nothing about a key to press to configure the BIOS (stupid sony). So I found [this](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB) but the wget ftp links for the two files arent allowing me to login anonymously. So if anybody has the two files or knows a place to get them it would be greatly appreciated.

---

### Post by CrispyFried on 2007-06-21
the BIOS POST (that allows you to get into the BIOS setup) runs before GRUB. its the very 1st thing that runs on boot. look for what key to press (sometimes it doesnt tell you as it hidden). try pounding on F1, F10, DEL etc while booting. you usually only have a couple seconds time.

when its configrred to try the CD as 1st boot device mine tell me to "press any key to boot from CD" on my laptop when a bootable CD is in the drive.

---

### Post by Jose Catre-Vandis on 2007-12-27
links updated here: [http://ubuntuforums.org/showthread.php?p=2237979#post2237979](http://ubuntuforums.org/showthread.php?p=2237979#post2237979)

---

