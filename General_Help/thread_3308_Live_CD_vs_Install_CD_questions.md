---
title: "Live CD vs Install CD questions"
date: 2004-11-05
forum: General Help
---

### Post by snorkel on 2004-11-05
Hi, I initially tried out the live CD and the grub menu looked much nicer with a graphical background and during boot up it displayed a nice framebuffer image with a boot progress bar.

My question is why the install CD does not do the same thing and how can I enable these eye candy features after I install?

Thanks,

Snorkel

---

### Post by oddabe19 on 2004-11-05
The live CD is based off of morphix.  There is no GUI splashscreen on booting in Warty, but there is one planned in Hoary (5.04).

To enable a pretty grub menu, look for a howto, you have to edit stuff in the /boot directory.

To enable a FB (framebuffer) startup with image, requires a kernel rebuild.

---

