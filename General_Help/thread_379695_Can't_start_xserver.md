---
title: "Can't start xserver"
date: 2007-03-08
forum: General Help
---

### Post by SirPaPa on 2007-03-08
Can someone help me please? I can't get back into my desktop after installing kerner 2.6.15.28-686. 
The xserver won't start even after the " sudo dpkg-reconfigure xserver-xorg " routine. 

I must be doing something wrong in configuring this.

Please help.](*,) ](*,)

Thank,you.
(I'm having to use my other drive to write this.)

---

### Post by lhtown on 2007-03-08
You could try the generic drivers. For instance, select "nv" instead of "nvidia" or you could try "vesa".

If that works, you can then uninstall your video drivers (Did you upload them manually instead of from the repository perhaps trying to get google earth or Compiz to work?) and then install them again from the repository and set them up again.

---

### Post by SishGupta on 2007-03-08
If you have manually installed your video drivers then you will have to reinstall each time you update the kernel as the driver kernel module needs to be recompiled for the kernel.

If you have used envy or downloaded the NVIDIA-LINUX-x86-yadayada.bin and installed that for your video drivers you must do it again.

The temp fix like suggested above is changing the xorg.conf video driver from nvidia to nv

---

