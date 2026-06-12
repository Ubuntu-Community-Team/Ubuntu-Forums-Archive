---
title: "deleted menu.lst"
date: 2008-05-03
forum: General Help
---

### Post by tom56 on 2008-05-03
Hi

I've been an idiot and deleted my /boot/grub/menu.lst. Is there an easy way to reinstall the default menu.lst? I tried sudo update-grub but it only adds entries for Ubuntu and leaves out Windows. Ideally, I want to run whatever command the Ubuntu installer runs to initially create menu.lst.

Thanks
Tom

---

### Post by Monicker on 2008-05-03
Try this:

[http://ubuntuforums.org/showthread.php?p=4710564]("http://ubuntuforums.org/showthread.php?p=4710564")

---

### Post by strabes on 2008-05-03
Reinstalling grub should fix this problem. See the link in my signature.

---

### Post by tom56 on 2008-05-03
None of those solutions work. GRUB itself is installed correctly, and if I run update-grub and reboot I can boot into Ubuntu fine. However, there is no option for Windows Vista. I know how to add the option manually but I'd rather do it the way the initial installer did it if possible.

---

### Post by ghost_ryder35 on 2008-05-03
> **tom56 said:**
> None of those solutions work. GRUB itself is installed correctly, and if I run update-grub and reboot I can boot into Ubuntu fine. However, there is no option for Windows Vista. I know how to add the option manually but I'd rather do it the way the initial installer did it if possible.
have you tried reinstalling grub? It auto detects what systems are installed and adds appropriate options to boot to them in the menu.lst file.  So if you reinstall grub it will rebuild your menu.lst file

---

### Post by tom56 on 2008-05-03
> **ghost_ryder35 said:**
> have you tried reinstalling grub? It auto detects what systems are installed and adds appropriate options to boot to them in the menu.lst file.  So if you reinstall grub it will rebuild your menu.lst file

I've tried that, reinstalling grub doesn't create a menu.lst at all. The easiest way to fix this would be to work out what command ubiquity uses to install grub and create menu.lst.

---

