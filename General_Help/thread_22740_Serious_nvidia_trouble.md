---
title: "Serious nvidia trouble"
date: 2005-03-29
forum: General Help
---

### Post by djauto on 2005-03-29
Have tried all kinds of things to get the nvidia-driver to work with Ubuntu Hoary. No luck so far, so I'm hoping someone can help me.

What I've tried so far (worth mentioning):
* Installing the ubuntu nvidia-glx package (v 6629) and running "sudo nvidia-glx-config enable". This made X crash, even with the 'Load "glx"' option disabled.
* Uninstalling all nvidia-stuff in synaptic, the installing some patched version of 6111 with nvidia script. This also made X crash, but after a system update X loaded, with the logo and all. Problem was games still used the old OpenGL-drivers. I replaced /usr/X11R6/lib/libGL.so(.1), /usr/lib/libGL.so(.1)  and /usr/lib/liGLcore.so(.1) with shortcuts to the respective nvidia-files. This made games segfault at startup.
* Installing official nvidia-packages (several versions), wich claimed they couldn't find the kernel-sorces, even with --kernel-source-path specified.
* Installing patched version of 7167, same trouble as Ubuntu 6629.

'Load "dri"' and 'Load "GLCore"' was disabled (commented), and I've tried numerous /etc/X11/xorg.conf options, like 'Option "NvAGP" "2"' and 'Option "RenderAccel" "true"'. Done "modprobe nvidia" also, and added "nvidia" to /etc/modules. I've tried a couple of other things too, but honestly I can't remember them all now... I HAD the drivers working at some point, pretty sure it was with the patched 6111, but after I re-set the resolution in xorg.conf X crashed again. I've used Mandrake until now, and I recall having problems with any other driver than some other patch of the 6111. There it worked, though, and it's also that I reset the BIOS-config since then, and I think I picked up somewhere that it might be something about the AGP->PCI stuff on the motherboard. I'm using a MSI K7N420 Pro with the nforce chipset, graphics chip is an onboard GeForce2 MX. I also tried with different kernels like the 686 and the K7.

Very nice if someone has some suggestion on what to do next. I've now reinstalled Ubuntu (again), updated, with a new and clean setup. Not sure what to try next, though, so any thoughts/ideas would be appreciated. Could try the 6111 from warty, for example?

---

### Post by djauto on 2005-03-29
Eh....nevermind.

Tried again with the patched 6111 drivers, and now it works! Problem was, of course, the refresh-rate, wich was loosely set from som other's xorg.conf. I've now set it to the rates found in the MANUAL of my monitor, and it's all working like a charm now.

Sorry, should have checked that first  :oops:

---

