---
title: "[SOLVED] Booting menu disappeared"
date: 2008-04-07
forum: General Help
---

### Post by sumitc on 2008-04-07
Okay,  here is what happened.

I installed Ubuntu as a dual-boot along with Windows XP SP2 about a year ago and it ran fine untill yesterday.

Yesterday I installed another version of Windows XP in a separate partition and the Ubuntu/Windows dual-boot menu has disapperead since then. When I start the menu now, only the Windows dual-booting menu is displayed. How can I get back the Ubuntu/Windows dual-booting menu?

I have Dapper Drake installed.

---

### Post by zvacet on 2008-04-07
[reinstall grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

---

### Post by dstew on 2008-04-07
The Windows boot loader wrote over the grub boot loader without asking permission. That is Window's way.

You need to re-install grub. [Here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") is a How-To.

---

### Post by sumitc on 2008-04-08
Thanks guys, I finally got it to work. I had to install GRUB to MBR for it to work Installing GRUB in the root partition wasnt goin anywhere and installing it at MBR did it. Thanks once again

---

