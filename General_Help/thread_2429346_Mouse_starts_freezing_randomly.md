---
title: "Mouse starts freezing randomly"
date: 2019-10-17
forum: General Help
---

### Post by 700 on 2019-10-17
PROBLEM:
This week my USB mouse started freezing randomly.
Reboot doesn't help. Power off only helps.

CONDITIONS:
- System: Ubuntu 18.04.3 LTS
- Machine: Dell Optiplex 990
- Processor: Intel Core i5-2400 CPU @ 3.10GHz × 4 
- GPU: GeForce GT 710/PCIe/SSE2
- GNOME: 3.28.2
- OS type: 64-bit
- Mouse: Logitech MX518 and ARES Gaming Mouse (both freeze)

QUESTION:
How to fix it, plz?

---

### Post by cruzer001 on 2019-10-17
Have you tried dropping back to previous kernel?  What video driver are you using?  Adder any new packages lately?

---

### Post by 700 on 2019-10-18
I didn't try to drop back to previous kernel.
Video driver (quote from Software & Updates): 
> NVIDIA Corporation: GK208B [GeForce GT 710]
Using NVIDIA driver metapackage from nvidia-driver-390 (proprietary)
I update my Ubuntu on a daily basis (using Software Updater, apt-get update/upgrade), but no extra unusual packages added.

---

### Post by 700 on 2019-11-14
EXTRA UPDATE:
My mouse keeps freezing after last kernel update: **4.15.0-70-generic x86_64**
It works well with: **4.15.0-64-generic x86_64**, but I'm not able to change the resolution to the correct one and the sound is not working as well.

---

