---
title: "Nvidia 8500GT driver problems on 64 bit Ubuntu 8.04"
date: 2008-07-03
forum: General Help
---

### Post by moesalim on 2008-07-03
Nvidia geforece 8500GT driver won't work on my 64 bit Ubuntu. I have tried using the unregistered driver, I have also tried using ENrgy, but I end up with a very low resolution and I have had to uninstall the driver. Because of this...I can't use desktop effects. I am an absolute beginner in Linux, so please take it easy on me, haha. Thanks

---

### Post by Vadi on 2008-07-03
I'm on an 8600gt here.

Have you tried going to System - Administration - Hardware Drivers, and enabling the video driver there?

---

### Post by loxaXcracker on 2008-08-15
I've got the same problem with my 8500GT (HP pavilion a6230). Nothing works from what I have tried...

---

### Post by mortenkjeldgaard on 2008-08-20
I have an nvidia GF8500GT card on a 64bit machine, and I had to download and compile the driver from nvidia's website to get accelerated graphics performance from the card.

* First, download the driver from nvidia's website. It comes in the form of a *.run file, which is actually a shell script.

* Boot up in "recovery mode", when the dialog comes up, choose to drop through to root.

* As root, do this:

sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run

answer the questions. I said "no" when it asked if I wanted to install nvidia's 32 bit OpenGL library.
I said "yes" when asked if you want to reconfigure with nvidia-xconfig.

* exit from the root shell, and choose to continue booting when asked.

I haven't gotten compiz to work yet, it just gives me the white screen that others have complained about.

---

