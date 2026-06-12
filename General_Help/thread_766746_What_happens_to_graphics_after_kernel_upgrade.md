---
title: "What happens to graphics after kernel upgrade?"
date: 2008-04-25
forum: General Help
---

### Post by brainiac8008 on 2008-04-25
Hi,

I am running 8.04 Hardy Heron off of the LiveCD.  I just downloaded the NVIDIA driver from their site for my GeForce 6150 SE.  The only way I could truly stop X was for me to screw up my xorg.conf file. :lolflag: I tried > sudo /etc/init.d/gdm stop and > sudo init 3 but X was really still running.  Once I got into the command prompt, I used > sh NVIDIA-Linux-x86-169.12-pkg1.run and I was able to install the driver fine.  Now I have Compiz running on the LiveCD.  If I install 8.04 to my hard drive, will I not be able to get into X when I do a kernel upgrade?  If so, what should I do to fix it?  Maybe editing the xorg.conf file, switching the driver to "nv", downloading the graphics driver from the NVIDIA site and installing it again will do the trick?

--Noah

---

### Post by kpkeerthi on 2008-04-25
You don't have to do all that **if** you install the driver from System -> Admin -> Hardware drivers on your hard-disk-installed-ubuntu.

---

