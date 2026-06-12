---
title: "GRUB background and Ubuntu splash screen changed.."
date: 2013-04-01
forum: General Help
---

### Post by Champlin93 on 2013-04-01
I recently tried out kubuntu-desktop on my computer and I was unaware that installing this would change the splash screen and GRUB menu into an ugly gray color.  I really only wanted to try out KDE and would like to change back to my Ubuntu splash screen and my nice purple GRUB background. What is the easiest way to do this?

---

### Post by grahammechanical on 2013-04-01
I do not know if this will work. Log into the Ubuntu desktop and open a terminal and run these two commands.
```
sudo update-grub
``` ```
sudo grub-install /dev/sda
``` That is if you only have one hard disk in your machine (sda) and Grub is installed in the MBR of sda.

The first command updates the Grub configuration files and as you are doing this from the Ubuntu desktop it may overwrite the instructions put there by the Kubuntu desktop. The second command writes Grub into the MBR of sda. We sometimes need to do this to get changes to Grub configuration to take effect. This will not remove the Kubuntu desktop.

Regards

---

