---
title: "adding new partition to the grub menu"
date: 2007-02-04
forum: General Help
---

### Post by 13east on 2007-02-04
i just recently added fedora core 6 as a triple boot and wanted to how to add that partition to the grub menu (already have ubuntu edgy and windows xp on the grub list).  i didn't add the grub menu that would've been normally installed with the fedora installation process, i just kept the the menu installed by ubuntu.  don't know if that matters or not but i thought to mention it.  i would really appreciate some help.  thx.

---

### Post by ZaphodBbl on 2007-02-04
Look in the /boot/grub/ directory for the file 'menu.lst'.  You'll have to edit it with sudo or become superuser.  In that file is the list of all the entries in the Grub menu, and pretty good examples of how to add your own entries.

You'll have to navigate to the /boot directory of the new installation and find out the exact name of the kernel that you're new OS uses, because you need that name to tell Grub what kernel to load.  If the drive the new installation is on is not on your desktop, you might need to enter it manually into your file browser in the format '/media/<drive name.', where drive name is something like hdb0 for the first partition of the second drive, hdb1 for the second partition on that drive, etc.  The rest of the information you need to get it to add can pretty much be copied from one of the other entries and edited to match your new kernel.

I hope this helps.  Good luck.

---

