---
title: "Projector is not detecting in Ubuntu 12.04"
date: 2013-01-29
forum: General Help
---

### Post by dmahesh22 on 2013-01-29
I'm using EPSON EB-S9 projector and it is connecting using USB cable to the Ubuntu system,but the problem is, Projector is not detecting by the system, following is some information regarding the my system.

```
 lspci | grep VGA

```output is:

> 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```
 sudo lshw -C video

```output is:

> *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f160(size=8)
I'm thinking that necessary drivers might be missing, how to install those ?

---

