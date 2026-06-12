---
title: "[SOLVED] Can't access windows after lubuntu install"
date: 2013-08-16
forum: General Help
---

### Post by carlos_vandias on 2013-08-16
Hello
I have a problem when booting my hp probook 4530s.
I've recently installed lubuntu, and then i can't access anymore my windows 7 installation from grub menu. Actually, when i select windows, the screen gets back to the grub menu, without any error.
However, i can access my lubuntu installation. I've noticed after launching gparted : 
[ATTACH=CONFIG]245415[/ATTACH]
Please Help is urgent :(

---

### Post by carlos_vandias on 2013-08-16
I don't how, but i fixed it up.
first :
sudo update-initramfs -u -k all
sudo update-grubThen:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

