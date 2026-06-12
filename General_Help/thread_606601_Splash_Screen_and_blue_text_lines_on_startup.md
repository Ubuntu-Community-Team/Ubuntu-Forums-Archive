---
title: "Splash Screen and blue text lines on startup"
date: 2007-11-08
forum: General Help
---

### Post by Zaff on 2007-11-08
Hey, this is purely a geek request with no real need but does anyone know how to make the ubuntu start screen display those blue text lines ?
Thanks

---

### Post by mcduck on 2007-11-08
Edit the /boot/grub/menu.lst file, and in the end of the kernel boot line remove the 'quiet'-option.

If you also add 'vga=792' you get Ubuntu to use 1024x768 resolution with 24-bit colors for boot and VTT's. Using 24-bit colors allows the boot text to use it's right color, brown, instead of blue..

---

