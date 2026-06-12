---
title: "How to install linux-restricted-modules without NVidia driver"
date: 2008-01-20
forum: General Help
---

### Post by TurtleSpit on 2008-01-20
Hello.  I had to go with the 169.04 nvidia driver to overcome the garbage driver provided in the synaptic package manager.  When I removed the old nvidia drivers, it uninstalled the linux-restricted-modules drivers.  How can i get them back without taking on the nvidia driver contained within?

Thanks.

---

### Post by dreadlord_chris on 2008-01-21
when you say it uninstalled the 'linux-restricted-modules drivers' - are you refering to the package named (just) **linux-restricted-modules**? If so, it's just a *meta-package*, don't worry about it.

Now, when you remove the old NVIDIA drivers, are you removing the **nvidia-kernel-common** package? This package gets installed with the **linux-restricted-modules-*** package - and is necessary. It's not actually the drivers, but the kernel interface that the drivers *hook* into.

---

### Post by TurtleSpit on 2008-01-23
nvidia kernel common actually is replaced by the 169.04 driver set from nvidia.  the pisser of having to remove the linux-restricted-modules is that it takes out my atheros driver, so now i have no wireless.  furthermore it takes out my audio driver, so i'm dead in the water there.  granted i could go to the trouble of finding these drivers individuallly and recompiling , but it would be a heck of a lot easier if i could find a package that didn't include these troublesome nvidia drivers.

---

### Post by ooopie on 2008-03-18
Any luck with this? I have the same problem...

nvidia-kernel-common = no xserver
no linux-restricted-modules = no sound, no wifi

---

