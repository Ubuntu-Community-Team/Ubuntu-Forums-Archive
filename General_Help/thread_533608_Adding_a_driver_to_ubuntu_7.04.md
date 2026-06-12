---
title: "Adding a driver to ubuntu 7.04"
date: 2007-08-24
forum: General Help
---

### Post by eashishkalra on 2007-08-24
Hi 

I want to add device driver for Ethernet LAN card from index to ubuntu 7.04. Driver for this card is available in new kernel 2.6.21. I have the driver file sc92031.c which i have taken from kernel 2.6.21.

How i can use this file to add driver for index Ethernet card to existing installation of ubuntu 7.04?
Can i do these without doing kernel rebuild or if kernels rebuild is required can someone explain the exact way to do this?

Regards
Ashish kalra

---

### Post by tpg on 2007-08-24
I would not expect to be able to "transplant" source code from one kernel version to another (it might work, but i'm not sure). The safest way to go is to download the latest stable kernel sources (which currently is 2.6.22.5) from [http://www.kernel.org]("http://www.kernel.org"), and compile the whole kernel from source.

It should then be possible to have both kernels installed side by side, and you can choose which to boot from the grub boot screen, if you set it up correctly.

Alternatively, you can wait for ubuntu 7.10 (due in October), which will have the latest kernel by default. (or you can run it in its current alpha/beta state, but this is not recommended, as breakage can, and does, occur)

---

### Post by eashishkalra on 2007-08-27
Hi tpg

Thanks for the reply. i want to try out by adding the driver file to current kernel and build before giving a try to new kernel. Can you please tell me how to get source code of current kernel from ubuntu and how to rebuild the kernel after modifying its source?

i am currently having ubuntu 7.04. Is it possible to get its kernel code as .deb file and rather than downloading it from direct internet connection using apt-get?

Regards
Ashish kalra

---

