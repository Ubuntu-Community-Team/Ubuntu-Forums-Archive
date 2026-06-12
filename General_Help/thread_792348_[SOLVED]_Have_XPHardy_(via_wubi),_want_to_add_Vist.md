---
title: "[SOLVED] Have XP/Hardy (via wubi), want to add Vista - help"
date: 2008-05-12
forum: General Help
---

### Post by hfxmike on 2008-05-12
Hi there,

I need to install Vista (ugh).

Right now, my main hard drive has XP, and I installed 8.04 via wubi. How should I go about installing Vista so I end up with a triple-boot system? I basically want Vista to be added to my grub menu.

rsvp
mike

---

### Post by inportb on 2008-05-12
Resize your Windows partition and pop the Vista disc. The installer should be able to add itself to the ntloader list. Wubi does not install GRUB. The process should be pretty similar to dual-booting XP/Vista without Ubuntu.

---

### Post by lookitseman on 2008-05-12
In my experience wubi actually does install grub...when you boot into Ubuntu from the windows boot menu, there's a 9 second countdown where if you push a key (enter i think), you'll go to the GRUB menu.  This would be used in case you install the real-time kernel or anything like that.

---

### Post by hfxmike on 2008-05-13
ok,

so should I just install Vista from the dvd, or boot into XP first? Not sure how to proceed...

---

### Post by ago on 2008-05-14
> **lookitseman said:**
> In my experience wubi actually does install grub...when you boot into Ubuntu from the windows boot menu, there's a 9 second countdown where if you push a key (enter i think), you'll go to the GRUB menu.  This would be used in case you install the real-time kernel or anything like that.


Wubi installs grub4dos, which is a special grub version that supports windows filesystems, but it does not replace the windows bootloader, on the contrary it adds an entry to the windows bootloader to then launch grub4dos whih in turns starts Ubuntu. Hence the fact that you have Wubi makes no difference to successive installation of windows. Of course if you install vista it will replace the XP bootloader, it might be possible to run XP from the vista bootloader which should then show the option to launch wubi. Or you can use easybcd to tune your vista bootloader.

---

### Post by hfxmike on 2008-06-11
Sorry I never provided an epilogue for my question. I installed Vista from within XP (on a free partition) with no problems whatsoever.

When I boot, I get:

Earlier windows
vista
ubuntu

when i select earlier windows, i get

XP
Ubuntu.

no prob booting into all three OS's

thanks
mike

---

