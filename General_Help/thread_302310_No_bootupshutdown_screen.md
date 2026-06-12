---
title: "No bootup/shutdown screen"
date: 2006-11-18
forum: General Help
---

### Post by ksac on 2006-11-18
Whenever I boot-up or shutdown all I get is a blank screen, as if I have no splash screen installed. Anyone else having this problem after upgrading from 6.06?

---

### Post by ksac on 2006-11-18
SOLVED

I changed my /etc/usplash.conf to:
xres=1024
yres=768

and I added vga=773 to my kernel options in /boot/grub/menu.lst

The boot splash appears in the top left corner of the screen.

---

