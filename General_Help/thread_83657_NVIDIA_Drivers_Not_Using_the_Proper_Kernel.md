---
title: "NVIDIA Drivers Not Using the Proper Kernel"
date: 2005-10-29
forum: General Help
---

### Post by jtwJGuevara on 2005-10-29
Hello All,

Here's my problem:

I have a GEForce2 GTS card which needs to use the nvidia legacy drivers.  These worked fine for the default 386 kernel that comes preinstalled with Breezy.  However, when I switched to the 686 kernel and removed the 386 kernel and all of its headers, I've observed that the nvidia legacy drivers from synaptic require the 386 kernel - so that is a no go.  My next attempt was a manual install.  I downloaded the 7174 drivers from NVidia (the last to support my card) and installed them manually.   It appears to install correctly, but the Nvidia module will not load.  

My hypothesis is that it is still trying to install the drivers and module for the 386 kernel and not my new 686 kernel.  Do you have any suggestions on how to make it install correctly for the 686 kernel?

Thanks.

---

### Post by drigloi on 2005-10-29
Try 

sudo apt-get install gcc-3.4
export CC=gcc-3.4

Breezy's kernel is built with gcc-3.4 whereas other packages are made with gcc-4.0. You need to tell which complier Ubuntu should use - to build a kernel module you definetly need the gcc-3.4.

---

### Post by jtwJGuevara on 2005-10-29
[QUOTE=drigloi]Try 

sudo apt-get install gcc-3.4
export CC=gcc-3.4

Breezy's kernel is built with gcc-3.4 whereas other packages are made with gcc-4.0. You need to tell which complier Ubuntu should use - to build a kernel module you definetly need the gcc-3.4.[/QUOTE]


This is a necessary step in order to install the Nvidia drivers manually, which I have tried.  The Nvidia drivers install successfully, but the module is still unloadable and thus I can't use Driver = "nvidia" in my xorg.conf.

---

### Post by jtwJGuevara on 2005-10-29
I should mention that when I modprobe the nvidia module, I get:

Error inserting nvidia (/lib/modules/2.6.12-9-686/volatile/nvidia.ko): No such device

---

### Post by jtwJGuevara on 2005-10-29
Ahah!

I managed to solve that one from instructions from another thread (I lost the URL while restarting gnome).

Here's what I did.  I removed everything 386 kernel related and everything nvidia related.  I then reinstalled everything 686 kernel related,  and namely the nvidia restricted modules for the 686 kernel.  When I then installed nvidia-glx-legacy, it worked like a charm.  I now have a 686 kernel with nvidia drivers :)

---

