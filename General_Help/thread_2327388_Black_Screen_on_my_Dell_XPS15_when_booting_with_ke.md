---
title: "Black Screen on my Dell XPS15 when booting with kernel &gt; 3.16.0-45 :("
date: 2016-06-10
forum: General Help
---

### Post by dean.frenz on 2016-06-10
I'm running Ubuntu 14.04 (can't upgrade yet coz need it for my work environment).
Booting with kernel 3.16.0-45 works fine. But when booting with newer kernels, the login screen goes black (startup sound plays). Not even going into terminal displays anything.

Anyone know why this is happening?

---

### Post by T.J. on 2016-06-11
Try adding nomodeset vga=0x318 to the startup parameters.  Nomodeset should disable the startup logo and vga=0x318 should force the display into standard VGA mode.  This will allow you to login and diagnose your problem.  Do you by chance have an Nvidia 800 or 900 series chipset?

---

