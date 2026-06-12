---
title: "Weird NVIDIA behavior - modules"
date: 2007-09-30
forum: General Help
---

### Post by thobel on 2007-09-30
It had been the case at some point that my x server would not start properly at boot -- it would give me this screen where it would query me for screen settings and driver settings. No matter what I did at this screen it would give me the screen back when I hit "OK". 

It turned out that when I killed x, removed the nvidia module, and reinserted it (via modprobe), I could start x.

So, currently my /etc/rc.local file reads

modprobe -r nvidia
modprobe nvidia

and now X starts properly at boot. I think by default the wrong nvidia module is being loaded. How do I change which module gets loaded at boot time, so I can remove this dirty hack from my system?

---

### Post by thobel on 2007-09-30
Solved -- just had to change /etc/default/linux-restricted-modules-common

---

