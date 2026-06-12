---
title: "Ubuntu tries to install onto my USB (that contains the installation media)"
date: 2016-08-05
forum: General Help
---

### Post by blastpower5 on 2016-08-05
[COLOR=#111111][FONT=Ubuntu]Hi,
I'm trying to dual boot my Dell xps 15 with Windows 10 and Ubuntu that has 512 gb ssd drive. I've created a boot device with a USB (Ubuntu 16.04) and created a 40 gb partition for Ubuntu. However, after selecting language in the installation process it says I need at least 8.5 gb disk space and that my computer only has 8.0 GB (which is the size of my USB stick I'm installing Ubuntu from). Running gparted in a live session also only shows my USB's storage, not my actual drive. Any suggestions would be helpful, thanks.[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-08-05
Is the Ubuntu live session loaded in EFI mode or BIOS/Legacy/CSM mode? Is Windows 10 fast start up disabled?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://ubuntuforums.org/showthread.php?t=2332735](https://ubuntuforums.org/showthread.php?t=2332735)

Regards

---

### Post by blastpower5 on 2016-08-05
Thanks for your reply.
Using the the paragraph "Identifying if the computer boots the Ubuntu DVD in UEFI mode" from the first link, it seems that the live sessions is loaded in EFI mode. Also, I have turned off fast startup from windows.

---

