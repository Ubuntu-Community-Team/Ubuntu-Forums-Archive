---
title: "Can't boot kernel"
date: 2007-10-15
forum: General Help
---

### Post by ZeldaFan on 2007-10-15
I have UbuntuStudio which comes with both the generic kernel and low latency kernel. I have Nvidia drivers which I installed through Envy when using my generic kernel. So whenever I boot into the generic kernel, xorg loads fine and everything goes well. However, then, when I want to boot into my low latency kernel, there is always a xorg error claiming it cannot load the Nvidia modules. How do I boot into my low latency kernel?

---

### Post by ZeldaFan on 2007-10-15
Apparently my nvidia.ko files doesn't exist in /lib/modules/2.6.20-16-lowlatency
I think I may just create an nvidia file and copy the nvidia.ko file that DOES exist in /lib/modules/2.6.20-16-generic/nvidia and hope it works. However some other files don't match either so I'm not sure what's wrong but I'm pretty sure my lowlatency kernel is messed up.

---

