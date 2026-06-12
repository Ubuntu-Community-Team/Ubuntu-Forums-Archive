---
title: "Xorg hogging memory (Xubuntu 16.04)"
date: 2016-09-14
forum: General Help
---

### Post by Firubat on 2016-09-14
After some time that the computer runs, Xorg starts using ridiculous amounts of RAM (1.2 GB on a 3GB system). On startup it uses only 50-80 MB (I'm using Task Manager to see the RAM usage).
Is there a way to stop this from happening?
Is there a way to reduce the memory without rebooting?

I'm using Xubuntu 16.04.1 on a Dell Inspiron N4030.

---

### Post by deadflowr on 2016-09-14
That's rather heavy.
What is the gpu?

---

### Post by Firubat on 2016-09-14
here is the output of [FONT=courier new]sudo lshw -C video[/FONT]

```
 *-display               
       description: VGA compatible controller
       product: RV710/M92 [Mobility Radeon HD 4330/4350/4550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:30 memory:c0000000-cfffffff ioport:e000(size=256) memory:fbe20000-fbe2ffff memory:fbe00000-fbe1ffff
```

---

### Post by Firubat on 2016-09-22
Ideas someone?

---

### Post by Firubat on 2016-10-18
I tried installing [Oibaf's graphic drivers]("https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers"), but the problem remains...

---

