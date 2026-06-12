---
title: "Vmware Server"
date: 2007-12-13
forum: General Help
---

### Post by gletob on 2007-12-13
I cannot figure out how to install Vmware Server in gusty Please help

---

### Post by fjgaude on 2007-12-14
What version of Ubuntu are you using?

The program VMware Server is in the depos, just use Synaptic to install.

---

### Post by gletob on 2007-12-15
7.10 and it not in the repos

---

### Post by HermanAB on 2007-12-15
Go to the VMware web site, find VMware Server, give them your whole pedigree, download the software and follow their instructions to the letter.  This has worked for me on many occasions.

Note that you can only install ONE virtualization system.  If you have played with something else before, first re-install your system and bring it purrrfectly up to date, install the kernel source and compile the kernel to make sure that the compiler and headers are configured right.  Then and only then install VMware Server.

Cheers,

H.

---

### Post by fjgaude on 2007-12-15
Come on, folks! I just checked both the 32- and 64-bit repos using Synaptic and they both show the vmware-server, latest 1.0.4 versions.

I've never had to compile any kernel to get vmware working correctly. One thing you have to completely remove any reference to an old vmware, server or player, before you can install a new one. I did that by again using Synaptic, going to the "Mark for complete removal" menu to get rid of all the configs, etc. That does it.

---

