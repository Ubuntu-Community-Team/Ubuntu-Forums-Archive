---
title: "Hardware Monitoring-Testing tools in boot"
date: 2007-11-20
forum: General Help
---

### Post by arigram on 2007-11-20
The decision to include Memtest86+ at the default boot menu is brilliant and I would like to expand the idea with more tools to monitor and test my hardware. How can I set up a boot menu item to include stress testers such as CPU Burn-in and MPrime and monitors such as lmsensors and the like? It would be a great assistance for OC and system stabillity testing not to have to wait for the OS to boot and risk corrupting it during settings testing.

---

### Post by ian dobson on 2007-11-21
Hi,

I think you can forget it. MEMTEST86 can run without loading an operating system/it contains enough code to run as a mini operating system that can "just" check memory.

All the other programs you've spoken about require an operating system to be loaded/kernel modules.

The only thing you could try an do is create a mini kernel that only includes enough drivers/kernel modules to get the system to boot and then load you tools.

Regards
Ian Dobson

---

### Post by arigram on 2007-11-21
Thank you for the advice.
Yes, I figured out as much, that is the need to load the kernel, not unlike how LiveCDs work.
Unfortunately I am new to Ubuntu and relatively new to Unix/Linux so I am not capable of
doing something like that without some instructions or pointers.

Anybody interested in helping out with this "project"?

---

