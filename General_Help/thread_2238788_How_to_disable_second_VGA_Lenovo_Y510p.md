---
title: "How to disable second VGA Lenovo Y510p"
date: 2014-08-10
forum: General Help
---

### Post by alex237 on 2014-08-10
[TABLE="class: full-html-diff, width: 900"]
[TR="bgcolor: transparent"]
[TD="class: post-text, bgcolor: transparent"]I have a Lenovo Y510p with NVIDIA GeForce GT 755M SLI and I installed Ubuntu 14.04.1 today. Usually I do a check for software/hardware compatibility, so I read in many places that I won't be able to run the SLI (yet). I don't want to use Bumblebee. So I have come to rest with the idea, but there is a problem. I want to get into a kind of a power saver mode (I've already done that by installing cpufreq).
My real concern is that while in win 8 I can just access device manager and disable the second VGA, with Ubuntu this is not the case. I should probably mention that I have changed the VGA drivers in software and updates -> additional drivers from using X.org X server(nouveau) to using nvidia binary driver (331.38).
The first problem is checking if the video cards are both working. I have read in some places that lspci | grep VGA is the right way to do it, which yields:
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 755M] (rev a1)
This suggests that there is only one VGA running. However, I can clearly hear the fan from the one in the ultrabay (secong VGA). Furthermore, lshw -class display yields
[COLOR=#405A04] *-display               
       description: VGA compatible controller
       product: GK107M [GeForce GT 755M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:50 memory:d3000000-d3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:5000(size=128) memory:b2000000-b207ffff

*-display
       description: 3D controller
       product: GK107M [GeForce GT 755M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:51 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:4000(size=128)
[/COLOR]On top of that, when I access NVIDIA X server settings, it shows gpu0 and gpu1, both having temperature which shows that are working.
My questions are:
[COLOR=#405A04]1[/COLOR].**[COLOR=#405A04]What is the correct way of seeing which video card is working[/COLOR]**
[COLOR=#405A04]2.[/COLOR]**[COLOR=#405A04]How can I disable it (the second one).[/COLOR]**
Please be a bit more detailed, because I have only joined the Ubuntu community as of today :)[/TD]
[/TR]
[/TABLE]

---

### Post by alex237 on 2014-08-10
bump

---

