---
title: "Nvidia-glx on Edgy-Gamma Problem?"
date: 2007-04-08
forum: General Help
---

### Post by apollo2011 on 2007-04-08
I am trying to get the nvidia-glx driver to run on my Kubuntu Edgy computer that has an nVidia GeForce3 Ti200 graphics card and a Dell 1702FP (Digital) monitor.

I had it working on previous versions of Ubuntu and on Edgy specificially. However, a few months ago I booted up after what I believe was a kernel update was installed, and X didn't load. I reverted back to the generic nv driver and got X running again, but without 3D support.

Several times since then I have messed around with the drivers (nv, nvidia-glx, nvidia-glx-legacy, and various versions of the nvidia driver as downloaded from the nvidia site). Either the driver doesn't run, runs with funny colors, or the installation insists that my card is not supported by the main driver and that I must use the legacy driver. The legacy driver then insists my card is not supported by the legacy driver.

Right now, I have the nvidia-glx package installed with the system fully up-to-date, and when I load X and KDE, the color scheme is off. I have attached a screenshot and my Xorg.conf.

---

