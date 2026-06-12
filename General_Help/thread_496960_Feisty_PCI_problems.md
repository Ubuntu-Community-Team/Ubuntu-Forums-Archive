---
title: "Feisty PCI problems"
date: 2007-07-09
forum: General Help
---

### Post by curiousben on 2007-07-09
Hello, 

I'm running Feisty 2.6.20-15-server on a desktop. I have a NIC with a RealTek 8139 chip. I cannot get network connectivity, and I suspect it is power problems regarding my PCI bus. This machine works fine with connectivity in Windows. I have run previous Linux distros successfully, though without ACPI working. 

This problem is over my head and I was wondering if you guys could help me out. I've attached dumps which I thought may be useful. 

Note that in the dump that the IRQ of eth0 is different when ACPI is on and when it is off. I believe the correct value should be 5 (just a guess from what I can tell from the early BIOS screens that precede grub starting up)

I cannot ping anything except 127.0.0.1 successfully, let alone get connection. Please help.

Ben

---

