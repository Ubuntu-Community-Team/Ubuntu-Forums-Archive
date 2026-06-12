---
title: "deleted /lib/modules/2.6.8.1-3-386/..please help"
date: 2004-12-05
forum: General Help
---

### Post by flamesrock on 2004-12-05
Hi, I was trying to install the kernal source. Strangely, the only source on synaptic is for 2.6.7..when ubuntu is running 2.6.8

Anyways, in the process of trying to recompile, I deleted /lib/modules/2.6.8.1-3-386/ permanently. How can I get it back?

-thanks

---

### Post by az on 2004-12-05
1- Don't panic.
2- Don't reboot.
3- sudo apt-get install --reinstall linux-image-2.6.8-1-386(whatever the version number is...)

Also, it is linux-source-2.6.8...  Kernel-source is a debian package.  Linux-source is an Ubuntu package...

---

