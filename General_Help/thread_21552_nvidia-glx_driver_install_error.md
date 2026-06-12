---
title: "nvidia-glx driver install error"
date: 2005-03-22
forum: General Help
---

### Post by pvoce on 2005-03-22
While installing through Synaptic the nvidia-glx driver, I receive the following error:

E: /var/cache/apt/archives/nvidia-glx_1.0.6629-0ubuntu23_i386.deb:  subprocess pre-installation script returned error exit status 2

This happens while unpacking.  I believe it to be a package problem, but I cant google or forum any other sites or fixes for the file.  Any ideas?

PV

---

### Post by pvoce on 2005-03-23
Found the problem.

Apparently, Ubuntu likes to install ATI drivers during install, which of course clahsed with the nvidia glx drivers. ](*,) 

Sorry for the waste of bandwidth...

PV

---

