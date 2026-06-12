---
title: "Grub problems hda2 unmountable"
date: 2007-07-25
forum: General Help
---

### Post by Flamespectre on 2007-07-25
I have been trying to install Ubuntu and I cant boot with grub, something about "Error 17: Couldnt mount selected partition" or something similar. There are two hard drives present, and the installation is a default clean install on hard drive 2, Any ideas?

---

### Post by logos34 on 2007-07-25
here's a detailed explanation:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

If you switched the bios boot order since install it may very well be the root designations.  

Try booting to the grub menu screen and hit 'e' key on the ubuntu kernel.  Highlight 'root' line and switch from (hd0,x) to (hd1,x) or vice versa (x being your root partition #).  Hit Enter after each change and 'b' to boot.  If it works then make the change permanent once you get the ubuntu desktop by editing /boot/grub/menu.lst.

---

