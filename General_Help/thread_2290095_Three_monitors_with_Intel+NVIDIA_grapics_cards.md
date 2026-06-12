---
title: "Three monitors with Intel+NVIDIA grapics cards"
date: 2015-08-09
forum: General Help
---

### Post by gingaz on 2015-08-09
Hi,

How do I set up three monitors with two graphics cards on Ubuntu 15.04 (64)? 
To my understanding, Bumblebee can achieve this. Thus I installed it, but it complaints that no integrated graphics card could be detected.

No trace of the third monitor and the integrated card anywhere in Ubuntu options.
Messa utils are there, nvidia drivers are working just fine (proprietary 346).
In BIOS, the integrated graphics card is set to 'always enabled'.
I can detect the integrated gpu with lshw [1]. 

Not really sure what is missing. Any hint is much appreciated.

The hardware: i7-2600; GeForce GTX 550 Ti/PCIe/SSE2.
Both graphics cards each have two DVI outputs. 


Thanks!
Gin

[1] sudo lshw -C display:

```
  *-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:42 memory:f8000000-f9ffffff memory:d0000000-d7ffffff memory:d8000000-dbffffff ioport:e000(size=128) memory:fa000000-fa07ffff
  *-display UNCLAIMED
       description: Display controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:fa400000-fa7fffff memory:c0000000-cfffffff ioport:f000(size=64)
```

---

