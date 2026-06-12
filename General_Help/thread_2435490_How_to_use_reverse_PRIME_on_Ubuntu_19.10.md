---
title: "How to use reverse PRIME on Ubuntu 19.10"
date: 2020-01-21
forum: General Help
---

### Post by quantumpie on 2020-01-21
I heard that Nvidia now supports PRIME offloading with their v435 and it's included in Ubuntu 19.10. I was hoping I would finally be able to use my dGPU solely for displaying my monitor while everything else was on the iGPU (I have a Thinkpad P1 which only has the ports connected to the dGPU). Unfortunately I learned that what I was looking for was actually reverse PRIME which isn't supported by the proprietary drivers. According to the [Arch wiki]("https://wiki.archlinux.org/index.php/PRIME#Reverse_PRIME") and other sources, the open-source Nouveau drivers support this but I don't know how to proceed. Do I need to uninstall the proprietary to install Nouveau or can both be installed? Once I install nouveau, what do I do to enable reverse PRIME? The Arch wiki doesn't make it very clear. I appreciate any help given!

---

