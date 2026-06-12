---
title: "Screen Flickering on HDMI"
date: 2019-04-21
forum: General Help
---

### Post by theonlytalkinggoat on 2019-04-21
I just attached another monitor to my laptop through HDMI and it is causing the main screen of the laptop to start flickering. It seems it does it when I click with the mouse, either the touchpad or the mouse. 

00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
	Subsystem: Toshiba America Info Systems 4th Gen Core Processor Integrated Graphics Controller [1179:f920]
	Kernel driver in use: i915

  *-display                 
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:33 memory:b2000000-b23fffff memory:a0000000-afffffff ioport:5000(size=64) memory:c0000-dffff

---

### Post by theonlytalkinggoat on 2019-04-22
I figured out this happens when I place a monitor above another. For instance, monitor 1 is a laptop, on my desk. Monitor 2 is an external monitor, sitting above. If I arrange the monitors side-by-side, in the display manager, it stops flickering. Any idea why?

I figured out it was the Gnome top panel causing the flicker. When I moved the panel to the top-most monitor the lower monitor's flickering instantly stopped.

---

