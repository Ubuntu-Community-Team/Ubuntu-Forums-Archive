---
title: "Only detecting one external monitor but both displaying and are mirrored"
date: 2015-06-24
forum: General Help
---

### Post by Harry_Goodman on 2015-06-24
Hi Guys.

Bit of background:
    I am an IT technician with 5 years of experience and at 21 years of age, probably 16-18 years of tinkering experience. I finally took the plunge and installed linux (14.04), but am having some issues. I have a Dell Latitude E5450 which is plugged into a docking station. This then outputs to 2 monitors. In display settings, only one monitor is displayed, as well as the internal display which is set to off. What's weird is, the 2 displays are both on and functioning, but they are mirrored and obviously as only one is listed in display settings, it's pretty impossible for me to set these to extend instead of mirror. This is also the same in ARandR. Does anybody have any suggestions. 

lshw -c video outputs the following:
    *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:64 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64)

---

