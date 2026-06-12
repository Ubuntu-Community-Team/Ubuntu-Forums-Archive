---
title: "Gutsy kernel recompilation problem"
date: 2007-11-27
forum: General Help
---

### Post by Benfr on 2007-11-27
Hi

I need to modify certains options in the standard gutsy kernel. So, I downloaded the sources (apt-get install linux-source), and let's go :

```

cd /usr/src
tar xjvf linux-source-2.6.22.tar.bz2
cd linux-source-2.6.22
sudo cp /boot/config-2.6.22-14-generic .config
sudo make menuconfig
sudo make-kpkg clean
sudo make-kpkg --initrd --revision=k7.raid kernel_image kernel_headers modules_image

```
And it gives me two packets : linux-image-2.6.22.9_k7.raid.deb and linux-headers-2.6.22.9_k7.raid.deb
But it's not the same version that the original gutsy kernel (2.6.22.9 instead of 2.6.22-14-generic). So linux-restricted-modules doesn't work anymore, and I loose my nice double screen :p

How can I do to get a 2.6.22-14-generic kernel ? Why this -14 at the end of kernel version, why not a point (.) instead of - ?

Thank you !

Ben

---

### Post by Benfr on 2007-11-28
Up :)

---

### Post by geraldm on 2007-11-28
The "-14" suffix provides a debian suffix for the source.  That number increments whenever there are changes to the package TOPDIR/debian/.. code.  The suffix is not related to the 
"2.6.22.9" as the last portion is dropped.  If the version of the kernel were to increment 
again, and a new source is released, there would be an increment to the debian suffix portion and the kernel version would still be "2.6.22" followed by the new suffix "-15"
As for your linux-restricted-modules not working, it may be related to your not selecting the
options needed to load and/or run a restricted-module when you made changes to various
kernel options you selected.  

Gerald

---

