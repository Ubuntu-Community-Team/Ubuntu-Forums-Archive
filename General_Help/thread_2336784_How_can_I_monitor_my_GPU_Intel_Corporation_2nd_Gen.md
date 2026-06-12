---
title: "How can I monitor my GPU: Intel Corporation 2nd Generation"
date: 2016-09-11
forum: General Help
---

### Post by user3514 on 2016-09-11
Hi,

What software would you suggest to monitor my GPU:

```

# sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:25 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)

```


Thank you

---

### Post by ajgreeny on 2016-09-11
Monitor it for what?

What exactly do you want to know about the graphics chip?

---

### Post by user3514 on 2016-09-13
I am running BOINC on my computer and need to know which percentage of my GPU is used overall.

Thank you

---

