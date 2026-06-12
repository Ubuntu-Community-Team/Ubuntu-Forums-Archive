---
title: "How to get the installer of a driver embedded in Ubuntu?"
date: 2015-09-03
forum: General Help
---

### Post by sab7 on 2015-09-03
My condition is quite weird. So, I have a laptop with Ubuntu and a PC with Lubuntu; and I need to use my webcam and my printer at home. The webcam is automatically recognized by Ubuntu, and my printer vendor (Brother) offers support for Linux, but explicitly says that there is a scanning problem with Ubuntu 11.1+, and, although the company explains a solution, it does not work. So, I would like to install a non-ubuntu-based distribution on the PC only, setup the printer's drivers and setup (if possibile) the webcam's drivers.
Is there a way to "find" the driver setup on my hard disk in which Lubuntu is installed?
Will it works for a debian/fedora/puppy based distribution?
If it will not works, I will buy another cheap scanner. Or another cheap webcam.

---

### Post by ian-weisser on 2015-09-03
A 'driver' in Windows is a 'kernel module' in Linux.
Generally, kernel modules are compiled anew for each version of the kernel. So unless your non-ubuntu-based distribution uses the same kernel version, the Ubuntu kernel modules may not work.

I would recommend a compatible new scanner.

---

