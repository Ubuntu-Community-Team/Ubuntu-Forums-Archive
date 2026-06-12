---
title: "Poor performace with Nvidia driver 6629"
date: 2005-03-19
forum: General Help
---

### Post by dillweed on 2005-03-19
Hi,

I've installed the nvidia drivers in hoary from apt-get and have it successfully running on my system.  In some informal tests (glxgears) I was only able to get about 4550 FPS.  I find this odd because I am dual-booting with Gentoo while I play with ubuntu.  In Gentoo I am able to get 6550 FPS in Gentoo.  That's a 2000 FPS difference and something that I would like to retain!!!!  I know that glxgears isn't the best test, but I made sure that the window was exactly the same size so I hope that isn't the problem.  I am also using a 686 kernel in Ubuntu.  In both systems there was no background stuff going on and both xorg.conf were identical as far as the driver section is concerned.  I'm really curious as to how I can get those FPS back in ubuntu or if anyone has any tips on how I can remedy this.

Thanks,
Dillweed

BTW my graphics card is a Geforce 6600GT with 128 megs of ram

---

### Post by alastair on 2005-03-19
Compare the logs and the configs i.e.

/var/log/Xorg.0.log
/etc/X11/Xorg.conf

or, for XFree86 :

/var/log/XFree86.0.log (I think ... I forgot)
/etc/X11/XF86Config

Anything different? Seems the obvious thing to do.

---

### Post by dillweed on 2005-03-19
The xorg.conf are the same.  I've thought that might be the case, but it wasn't.

---

### Post by alastair on 2005-03-20
What about the logs? Did you compare? Use a GUI diff tool e.g. meld.

Also, are they the same s/w versions on both machines? i.e. same version of XFree or Xorg?

---

