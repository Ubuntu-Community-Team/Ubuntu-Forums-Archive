---
title: "Changing the grub default FROM WINDOWS"
date: 2008-04-07
forum: General Help
---

### Post by kevpatts on 2008-04-07
Hey all,

I often remotely control my dual boot PC using VIM and I would like to be able to switch OS between Windows and Ubuntu and reboot. Is this possible? I currently use the "default saved" in my manu.conf file but I would somehow need to change the saved value from both windows and Ubuntu before rebooting.

Has anyone tried to get this working before?

Kevpatts

---

### Post by justleen on 2008-04-07
you would have to edit the menu.list every time before you reboot, to change the value. But yes, it is possible i'd say

---

### Post by kevpatts on 2008-04-07
Hey man, I'm not looking to edit the menu.conf file because this file doesn't store what the saved default is (I believe). I don't know where that info is stored but that's what I'd need to change. Would I have to install ext3 drivers for Windows and manually edit it? I was hoping there was some Windows GUI that'd do it.

---

### Post by girishv on 2008-04-07
Unless you have created a boot partition and made it fat32, it is not possible to do this directly, since, grub reads the menu.lst from this partition. One another way of achieving the same is to
install ext2 explorer in windows. For some strange reason, I found that this almost destroyed my root partition and do not recommend.

Girish

---

### Post by kevpatts on 2008-04-07
but menu.lst stores the fact that I save the default each time, it doesn't store the actual default value.

---

### Post by pointone on 2008-04-09
According to [the GRUB manual]("http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html#Invoking-grub_002dset_002ddefault"):

> The program grub-set-default sets the default boot entry for GRUB. This automatically creates a file named default under your GRUB directory (i.e. /boot/grub), if it is not present. This file is used to determine the default boot entry when GRUB boots up your system when you use `default saved' in your configuration file (see default), and to save next default boot entry when you use `savedefault' in a boot entry (see savedefault).

---

