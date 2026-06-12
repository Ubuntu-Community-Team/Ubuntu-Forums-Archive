---
title: "Force Ubuntu to use second graphics card"
date: 2014-06-28
forum: General Help
---

### Post by dave-gerdeman on 2014-06-28
I have a KVM vga passthrough setup that works quite well, with Ubuntu using the integrated graphics in my Intel processor and my VM using the HD7970 in PCI-e slot one.  I bought a low end nvidia card to use instead of the integrated graphics.  The nvidia card is in PCI-e slot 2.  So far, I have been unable to get Ubuntu to use the new card for display output.  It is reading it as using the gallium3d driver, even after installing the proprietary nvidia drivers.  After disabling the integrated graphics, I have not been able to get the new card to output anything.  

Is there any way to get ubuntu to completely ignore my first card and force it to use only the second card?  I am already blacklisting the proprietary and open source AMD drivers and I added it to the pci_stubs list as well.

---

### Post by dave-gerdeman on 2014-06-29
help me ubuntuforums, you're my only hope.

Swapping the video cards isn't an option.  The AMD card is too long and the SATA connections get in the way.

---

### Post by MrSteve on 2014-06-29
you could blacklist the integrated graphics card ...

[https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

---

