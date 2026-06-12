---
title: "Installing Fedora 8 now!?"
date: 2008-06-14
forum: General Help
---

### Post by rivalslayer on 2008-06-14
I have installed Ubuntu 8.04 Hardy in my system. I have my /boot in a separate 98mb partition. Now I want to install my Fedora 8 without affecting the Ubuntu 8.04. Should I superpose the /boot partition between Fedora and Ubuntu. Or, should I omit the grub bootloader installation, and then manually add a GRUB entry in the /boot/grub/menu.lst in ubuntu for Fedora 8. What should I do? Pease help...!!!

:confused:

---

### Post by f4k1r on 2008-06-14
When I had opensuse and fedora 7,I manually added opensuse in fedora's grub after installation.

---

### Post by Fingel on 2008-06-14
I would not share the /boot partition. Its a bad idea because the distros might be using different versions of kernels. When you install fedora 8, it should automatically pick up on your ubuntu partition and add it to grub. no need to manually add it. But if it doesnt, it shouldn't be that hard to do.

---

