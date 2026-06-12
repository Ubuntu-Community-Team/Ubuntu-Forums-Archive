---
title: "ndiswrapper installation w/ no internet"
date: 2005-10-25
forum: General Help
---

### Post by azuiden on 2005-10-25
so i have a difficult situation

i need to connect to my network to make machine operable to make it worth using

but i need ndiswrapper to connect my computer to the network

and the hardware needs the ndiswrapper


things i can't do:
get a new card (i would just as soon as download a new distro)
set up a wired connection

---

### Post by az on 2005-10-25
Ndiswrapper-utils is on the cd.  If you did a default install, it is actually cached on your hard drive and it won't even ask you for the cd when you tell it to install.  The kernel module is already in your kernel.

So, fire up synaptic, install ndiswrapper-utils and open a terminal to install your drivers

sudo ndiswrapper -i (filename.inf)

sudo modprobe ndiswrapper

---

