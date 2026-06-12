---
title: "Virtual terminals with Acer AO722"
date: 2013-03-08
forum: General Help
---

### Post by tarkawebfoot on 2013-03-08
I have an Acer AO722 and am running Ubuntu 12.04. I've gone through many configuration changes and the netbook works really well now except for one thing: no virtual terminals.

I've found posts that suggest this is a problem with the video drivers. Here is the hardware I'm running:

```
tarka@Cuddy:~$ sudo lshw -C video
[sudo] password for tarka: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Wrestler [Radeon HD 6290]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff ioport:4000(size=256) memory:f0400000-f043ffff



```

I downloaded and installed the fglrx driver and enabled it. Still no virtual terminals, though the video behaves differently under that driver. In both cases when I switch terminals, I get a black screen. But in both cases I can switch back to the primary (CTRL-ALT-F7) with no trouble. 

How can I get my virtual terminals running on this machine?

Thanx in advance

---

