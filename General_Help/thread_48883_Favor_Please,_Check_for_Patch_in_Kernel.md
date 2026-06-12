---
title: "Favor Please, Check for Patch in Kernel"
date: 2005-07-14
forum: General Help
---

### Post by springshades on 2005-07-14
Hi,

I'm looking to see if I can install ubuntu on my laptop. My laptop has an issue where the integrated RAM has bad memory addresses so I have to have either the Badram or BadMEM patch compiled into the kernel. I can't compile it myself due to the fact that the RAM is integrated into the motherboard, so comments like "patching the kernel is trivial" don't work here (I've gotten plenty of them).

Anyway, if someone can do me a favor that has the ubuntu kernel source package installed, you can see if the patch shows up in the .config file or do a make menuconfig and load the .config file from the source package and look in the kernel menu to see if it has the option of removing bad memory. This would help me tremendously. I just need to know if the kernel comes with that patch in the default install.

---

### Post by geearf on 2005-07-14
It does not seem to be in my .config, i guess you'll have to find it already patched, or patch it somewhere else :(

---

### Post by springshades on 2005-07-14
Thank you, this helps me quite a bit. I can always fall back to Mandrake (so far the only distro I've found with this patch built in the default kernel).  I'm just looking around at other possibilities. :)

---

### Post by geearf on 2005-07-15
Well you can still patch the kernel from Mandrake, and then use the net install for ubuntu with the kernel you've patched, it might work.

---

