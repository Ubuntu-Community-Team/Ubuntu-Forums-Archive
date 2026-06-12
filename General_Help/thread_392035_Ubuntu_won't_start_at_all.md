---
title: "Ubuntu won't start at all"
date: 2007-03-24
forum: General Help
---

### Post by crazydavythe1st on 2007-03-24
I can't get Ubuntu (Edgy Eft) to start. I've got my computer setup to start with the Windows bootloader and then when Linux is selected, to show GRUB. Everything has been working normally, and then today when I started my computer, Linux wouldn't start. It displays

"GRUB  "

and then freezes. The only thing I remember doing in Ubuntu yesterday was checking email and running aptitude update. I tried reinstalling GRUB using the guide at [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351). This didn't work either. I don't want to have to reinstall Ubuntu, as I've spent hours configuring things like my wifi device, installing Beryl, etc. Is there anything I could possibly do to solve this? Thanks in advance.

---

### Post by zvacet on 2007-03-24
Boot up  your CD and from login screen choose "Recover a broken system&#733;.Continue through these dialogs until you are prompted to choose your root device.It is probably second,because you are dual-booting.If you do it right you will see next window and "Reinstall GRUB boot loader" on it.Pick that option and you will be asked whereto put it.Type hd0.If all is O.K. choose reboot option.

---

### Post by crazydavythe1st on 2007-03-24
> **zvacet said:**
> Boot up  your CD and from login screen choose "Recover a broken system&#733;.Continue through these dialogs until you are prompted to choose your root device.It is probably second,because you are dual-booting.If you do it right you will see next window and "Reinstall GRUB boot loader" on it.Pick that option and you will be asked whereto put it.Type hd0.If all is O.K. choose reboot option.

Where can I find this option? When I put in my CD, the screen only shows Run Live CD/Install, Run Text Installer, and some other options, but there isn't anything that says Recover broken system.

---

### Post by crazydavythe1st on 2007-03-24
I got tired of trying to fix my existing ubuntu installation, so I deleted the partition and reinstalled it. The exact same thing is still happening. It's like GRUB is still there even after I delete the partition and recreate it. Is there a way to remove it completely so I can reinstall ubuntu and have it work?

---

