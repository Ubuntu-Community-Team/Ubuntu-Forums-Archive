---
title: "Only bottom half of screen visible after rotation - Asus T300 Chi"
date: 2015-06-27
forum: General Help
---

### Post by NCLI on 2015-06-27
When I rotate the screen using xrandr -o, right or left, only the bottom half of the screen is visible. Everything returns to normal after running xrandr -o normal.

I have no idea how to troubleshoot this, so any input would be appreciated.

---

### Post by cariboo on 2015-06-27
What graphics adapter and video driver are you using?

---

### Post by NCLI on 2015-06-28
Sorry about the late reply. Here is the info from lshw:
>   *-display               
       description: VGA compatible controller
       product: Broadwell-U Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64)

---

### Post by NCLI on 2015-06-29
Friendly neighbourhood bump.

---

### Post by chris137 on 2015-06-30
Just a stupid question for clarification:
Are you sure it's not just your dekstop-wallpaper that's not fitting on the screen correctly after rotating?

---

### Post by NCLI on 2015-06-30
> **chris137 said:**
> Just a stupid question for clarification:
Are you sure it's not just your dekstop-wallpaper that's not fitting on the screen correctly after rotating?

Yes, unfortunately.

---

### Post by NCLI on 2015-07-01
Anyone?

---

