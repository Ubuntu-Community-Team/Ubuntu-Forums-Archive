---
title: "stripes on display"
date: 2014-02-26
forum: General Help
---

### Post by oh my on 2014-02-26
Hi,

since this morning my screen is striped and I would like to ge those stripes removed. I didn't shut down the PC overnight, they simply "appeared" after reactivating the screen. The stripes do not appear during the booting procedure or BIOS but only at the login screen (and remain after login or I wouldn't mind).  I did upgrade to  3.11.0-17-generic recently but I had already rebooted in between. Moreover going back to 3.11.0.15 did not remove the stripes. 
I am using Kubuntu 13.10 and this is the output of lshw -c video:
```
$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:62 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

```

I've also attached a screenshot, in the hopes that you can see the lines there:
[ATTACH=CONFIG]250689[/ATTACH]

If anyone knows how to fix I'd be most grateful.

regards
myrti

---

### Post by lykwydchykyn on 2014-02-26
Are they subtle?  I don't see any stripes.  Are you sure it's not just your monitor?

---

### Post by tgalati4 on 2014-02-26
No stripes, but I do see flying elephants.

---

