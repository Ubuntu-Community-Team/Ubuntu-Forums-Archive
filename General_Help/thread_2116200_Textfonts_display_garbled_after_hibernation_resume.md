---
title: "Text/fonts display garbled after hibernation resume"
date: 2013-02-15
forum: General Help
---

### Post by AmirJamez on 2013-02-15
I have just installed ubuntu 12.04 LTS as a primary ex4 partition (as a sole OS) and set the swap partition over double my RAM which was 3 GB (Swap partition is currently 10 GB).

The thing that I just experienced is having the fonts and texts just garbled after resuming hibernation, I was wondering if there is an incompatibility with my graphic card driver or something else ?

[---> This is the Snapshot of the current OS view]("http://s11.postimage.org/64hyjsflv/Screenshot_from_2013_02_13_12_34_02.png")

P.S: Just to add that I have the Intel GM45 display driver chipset for graphic.(Further Information Bellow)

Thanks for your time,

Amir

 *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise
Linux amir-labtop 3.2.0-37-generic-pae #58-Ubuntu SMP Thu Jan 24 15:51:02 UTC 2013 i686 i686 i386 GNU/Linux
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

---

