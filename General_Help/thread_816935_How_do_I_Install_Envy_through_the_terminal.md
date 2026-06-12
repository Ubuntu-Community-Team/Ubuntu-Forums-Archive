---
title: "How do I Install Envy through the terminal?"
date: 2008-06-03
forum: General Help
---

### Post by Vigh on 2008-06-03
I tried installing Envy through the terminal, following the guide at Envy's website and it said unable to find package. Could some please help me out here. Thanks

---

### Post by StOoZ on 2008-06-03
maybe the proper repository list is not enabled in your sources.list

just go to the official site and download it from there.

---

### Post by pedro_orange on 2008-06-03
You may find this command useful:

```
apt-cache search package-name
```

So for Envy I'd summit like:

```
pedro@pedro-laptop:~$ apt-cache search envy
alsa-tools-gui - GUI based ALSA utilities for specific hardware
envyng-core - install the ATI or the NVIDIA driver
envyng-gtk - install the ATI or the NVIDIA driver
envyng-qt - install the ATI or the NVIDIA driver
fglrx-amdcccle-envy - Dummy package for easy transition
fglrx-control-envy - Control panel for the ATI graphics accelerators
fglrx-kernel-source-envy - ATI binary kernel module source
nvidia-glx-dev-envy - NVIDIA binary XFree86 4.x/X.Org driver development files
nvidia-glx-envy - NVIDIA binary XFree86 4.x/X.Org driver
nvidia-glx-legacy-dev-envy - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files
nvidia-glx-legacy-envy - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
nvidia-glx-new-dev-envy - NVIDIA binary XFree86 4.x/X.Org 'new' driver development files
nvidia-glx-new-envy - NVIDIA binary XFree86 4.x/X.Org 'new' driver
nvidia-kernel-source-envy - NVIDIA binary kernel module source
nvidia-legacy-kernel-source-envy - NVIDIA binary 'legacy' kernel module source
nvidia-new-kernel-source-envy - NVIDIA binary 'new' kernel module source
xorg-driver-fglrx-dev-envy - Video driver for ATI graphics accelerators (devel files)
xorg-driver-fglrx-envy - Video driver for ATI graphics accelerators
pedro@pedro-laptop:~$ 
```

So that tells me all the packages that contain the string 'envy'.
Then you just apt-get install the one you want.

---

### Post by Pjotr123 on 2008-06-03
Envy is in the Universe repository nowadays. Install it like this:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2)

So this makes life even easier.  :-)

Greeting, Pjotr.

---

