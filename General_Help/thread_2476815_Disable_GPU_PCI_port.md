---
title: "Disable GPU PCI port"
date: 2022-07-08
forum: General Help
---

### Post by jacthy on 2022-07-08
hardware
Lenovo Y720
GPU : GTX 1060
External GPU: RTX 3080

Ubuntu 18.04

I tried to disable the GTX 1060 for some reason.
I disabled in BIOS, but the two graphic card stopped working at the same time.
I tried to edit the file in sys/bus/pci/devices/0000:01:00.0(the bus PCI ID for GTX 1060). I try to turn the ./power/control to 'off'. I cannot edit it.
I also tried to use 'echo'to change the value of this file. it still didn't work.

Is there is any orther way to disable this GPU or the PCI port.

I will be appreciate for your help.

---

