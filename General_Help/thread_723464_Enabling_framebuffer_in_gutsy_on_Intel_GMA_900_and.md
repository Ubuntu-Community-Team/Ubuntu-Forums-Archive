---
title: "Enabling framebuffer in gutsy on Intel GMA 900 and/or 950"
date: 2008-03-13
forum: General Help
---

### Post by ergosteur on 2008-03-13
Hello,
I'm having problems getting my framebuffer consoles working in gutsy. I managed to get it working on 3 previous gutsy installs, but I can't remember how I did it. 
My consoles work in basic text mode on a fresh install.

My laptops are
1) an Acer Aspire 5570Z, with an Intel 943GML chipset and Intel GMA950.
2) Acer Aspire 3623 with Intel 910GML and GMA900.


Here's what I've tried so far:

1) modprobe vga16fb && modprobe fbcon
Produces random green rectangles in the vt1-6.

2) comment out vesafb, intelfb and i810fb in /etc/modprobe.d/blacklist-framebuffer and add vga=792 to menu.lst
vt1-6 show nothing but a blinking cursor in the top left corner.

also tried running update-initramfs -u after changing the blacklist, but not sure if that's necessary

3) used startupmanager GUI tool to change resolution and colour depth.

Does anyone know of a sure way to enable framebuffer consoles?

---

### Post by ergosteur on 2008-04-02
got it. 
[http://wirelessmike.bluekeep.net/2008/02/29/kubuntu-gutsys-splash-screen-fix/](http://wirelessmike.bluekeep.net/2008/02/29/kubuntu-gutsys-splash-screen-fix/)

---

