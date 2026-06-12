---
title: "NVIDIA TNT2 and Legacy Driver Issues on Edgy"
date: 2007-02-17
forum: General Help
---

### Post by plb on 2007-02-17
So I was able to get an old NVIDIA TNT2 card yesterday and it works fine with the nv driver but upon installing the legacy drivers...well that isn't so good. I installed via synaptic and I also gave envy a try. I've got a few blank screens also an error about "unknown module type, 6" Running depmod gives me this: 
"WARNING: Module /lib/modules/2.6.17-11-386/kernel/drivers/video/nvidia.ko is not an elf object"
The machine is an up to date edgy box. Anyone got some suggestions?

---

### Post by Erlander on 2007-02-17
I found the default drivers that are installed with a new installation are the best.

How you go back to them without a new install of ubuntu I don't know.

Rob

---

### Post by plb on 2007-02-18
I tried that, didn't work. Also tried installing legacy drivers straight off nvidia site which resulted in a blank screen.

---

