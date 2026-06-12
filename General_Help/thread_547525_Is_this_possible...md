---
title: "Is this possible.."
date: 2007-09-10
forum: General Help
---

### Post by Matt Jones on 2007-09-10
To install Wubi WITHOUT adding an extra entry to the boot loader.

So when I turn my computer on, I boot straight into Windows but then if I want to load Ubuntu I can run a file from my PC and the PC will reboot into Ubuntu automatically?

I only ask because there will be other users on the PC and they will not want to see a boot menu,

---

### Post by ago on 2007-09-10
The simplest way is to just lower the timout of the bootloader to 1 sec. Uninterested users will briefly see the menu as a flash, if you want Ubuntu, you just have to hit an arrow key in the first sec.

---

### Post by Matt Jones on 2007-09-10
Thinking about it, am I better off just doing a real install and using a boot disk instead of grub?

---

### Post by ago on 2007-09-10
> **Matt Jones said:**
> Thinking about it, am I better off just doing a real install and using a boot disk instead of grub?

You can do that with wubi as well, just put grub4dos on a floppy/usb key, then restore the windows menu.

---

