---
title: "Ubuntu 12.04 has bad performance in OpenArena compared to Windows 7"
date: 2014-03-12
forum: General Help
---

### Post by ivanovic.marko on 2014-03-12
I have same version od OpenArena on Windows and on Linux, they run on same machine, on graphic settings in OpenArena are same. But performance is better in Windows. But what really annoys me is black margins on the sides of screen which is not present in Windows, although is same monitor and same resolution is set. And also in Ubuntu everything is so much darker. I've adjusted brightness as much as I can, but everything is still too dark.
I don't have very good graphic card, but performance on Windows is great, why is that? Can this be fixed?
This is output of ```
sudo lshw -C display
```:

```
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fd780000-fd7fffff ioport:cc00(size=8) memory:d0000000-dfffffff memory:fd740000-fd77ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fd680000-fd6fffff
```

Thanks.

---

