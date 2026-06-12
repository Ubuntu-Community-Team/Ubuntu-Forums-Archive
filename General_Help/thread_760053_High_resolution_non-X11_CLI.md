---
title: "High resolution non-X11 CLI"
date: 2008-04-19
forum: General Help
---

### Post by radivx on 2008-04-19
Hi,
I need som help with graphics outside X.

I practially want something like this:
[http://gentoo-portage.com/up_img/img_800px/94.png](http://gentoo-portage.com/up_img/img_800px/94.png)

That includes:
A nice looking verbose boot (high resolution and color on the items).
A high resolution CLI outside X (maybe with background image ++?)

Any ideas where to start and how to manage this under Ubuntu? The stuff outside X11 is the only thing that other distros have and I miss from Ubuntu (even SuSE 9 had a nice verbose boot system with background and colors).

---

### Post by gsmanners on 2008-04-19
Outside of X, you'll need to change the kernel line in grub (menu.lst).

See: [http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

---

### Post by x1a4 on 2008-04-19
Hi,

The image uses **bootsplash**.  Ubuntu uses **usplash**.  Replace usplash with bootsplash.  Bootsplash is in the repositories, although a bit out of date.  To download the latest version and for information see [bootsplash.org]("http://bootsplash.org/")

---

### Post by radivx on 2008-04-20
The 1024x768 console using vga=791 works. However I still want the nice colors during boot saying green okays, and red fails. Why does Debain/Ubuntu not have these colors, but the majority of desktop oriented distros have?

---

### Post by gsmanners on 2008-04-20
I haven't tried it myself, but there is splashy.

[http://splashy.alioth.debian.org/wiki/](http://splashy.alioth.debian.org/wiki/)

---

### Post by ryanhaigh on 2008-04-20
> **radivx said:**
> The 1024x768 console using vga=791 works. However I still want the nice colors during boot saying green okays, and red fails. Why does Debain/Ubuntu not have these colors, but the majority of desktop oriented distros have?

I would guess because the ubuntu boot process uses a splash image rather than showing the detailed information by default. You could find the scripts that are producing the ok etc and change them to use colour outputs if you wanted. [http://tldp.org/LDP/abs/html/colorizing.html](http://tldp.org/LDP/abs/html/colorizing.html) has info on changing output colour in bash scripts.

---

### Post by Whiffle on 2008-04-20
What you're looking at there is a high resolution framebuffer.  

[http://joeamined.wordpress.com/2008/02/25/enabling-high-resolution-console-in-ubuntu/](http://joeamined.wordpress.com/2008/02/25/enabling-high-resolution-console-in-ubuntu/)

---

