---
title: "Server Installation - A question about screen resolution"
date: 2007-05-17
forum: General Help
---

### Post by tkambler on 2007-05-17
I'm running Ubuntu 6.06.1, server installation. I'm not using any sort of window manager, just the terminal. I'm curious... Is there any way to increase the screen resolution of the terminal that I'm using? I've never done that before and thought I'd ask.

Thanks!

Tim

---

### Post by HomerSimpson748 on 2007-05-17
You should be able to append "vga=###" at boot to change the vga mode.

There is a pretty good article explaining it here...
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

Modify your /boot/grub/menu.lst to make permanent. Very useful for LCD displays where the edges of the terminal is cut off.

---

### Post by tkambler on 2007-05-17
Worked like a charm, thanks.

---

