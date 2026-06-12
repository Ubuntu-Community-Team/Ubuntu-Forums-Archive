---
title: "Print Drivers"
date: 2007-02-26
forum: General Help
---

### Post by freemart on 2007-02-26
Do I need special drivers to make a printer work on 64 bit Ubuntu?

I have three computers running Ubuntu 6.10. Two are 32 bit and another is 64 bit. The printer is an HP 1120C. The two 32 bit computers print o.k.

The new 64 bit does not print correctly. Ubuntu detects the printer and installs the driver. But it prints one line of garbage. I also have Windows X64 XP Pro and Windows XP 32 bit XP Pro installed on the same computer. Printing works fine on both so hardware must be o.k.

Any ideas?

---

### Post by freemart on 2007-02-27
More on my driver problem.

I booted from a 32 bit install disk, Kubuntu 6.10 Beta. Printer install worked o.k. What is different with the 64 bit install versions?

---

### Post by freemart on 2007-02-27
Found the problem. It is a bios setting on the Asus S8N-VM CSM/NBP mother board. Do not setr up the parallel port for "ECP". Rather set it up for "NORMAL".

---

