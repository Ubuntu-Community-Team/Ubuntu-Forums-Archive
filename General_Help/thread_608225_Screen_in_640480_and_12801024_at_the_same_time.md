---
title: "Screen in 640*480 and 1280*1024 at the same time"
date: 2007-11-09
forum: General Help
---

### Post by dominikgeisler on 2007-11-09
Hi, 

I just installed Ubuntu 7.10 x86-64 on my machine (AMD 64, integrated Radeon graphics (a cut-down version of R300, don't know the name). The problem is kinda weird; I can move windows over the entire screen, but the task bar and the bar on top only occupy the 640*480 area. In preferences -> screen resolution I can only select 640*480, although the screen really is running ar 1280*1024. Does anyone have an idea? 

sudo lshw -C display returns: 
  *-display               
       description: VGA compatible controller
       product: RS480 [Radeon Xpress 200G Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga bus_master cap_list
       configuration: latency=64 mingnt=8

Thanks, 

Dominik

---

