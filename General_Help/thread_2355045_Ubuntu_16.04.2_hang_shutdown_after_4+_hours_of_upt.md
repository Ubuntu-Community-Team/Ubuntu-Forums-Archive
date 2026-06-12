---
title: "Ubuntu 16.04.2 hang shutdown after 4+ hours of uptime"
date: 2017-03-08
forum: General Help
---

### Post by renebarbosa on 2017-03-08
After upgrading my laptop (Dell Inspiron 5447) to Ubuntu 16.04.2 I can't shut down after a few hours using the system (4+ hours). It hangs in Plymouth and stays that way until I force the shutdown by pressing the Power Button. As this is a common bug (there are tons of questions on the Internet) I tried to fix it, but none of my attempts were effective. 

Already tried:


1. Boot with acpi=force, acpi=noirq and pci=noacpi
2. Disable Swap
3. Run 'sync' before reboot or shutdown
4. Use another kernel version (4.7, 4.8, 4.9 and 4.10 from mainline)
5. Disabling USB 3.0
6. Disabling TLP
7. Install AMDGPU-PRO 16.60


The most interesting thing is: I can shutdown/reboot normally using 14.04 and the kernel from Xenial HWE and it's because of that I believe this is a systemd bug.


My Machine Specs:


Dell Inspiron 5447 - BIOS A10
Intel Core i5-4210 Processor
8 GB RAM
480 SSD Sandisk
Hybrid Graphics (i915/amdgpu - Radeon R7 M265)


I also posted a bug against the systemd package (# 1663794), but I did not get any help from there.

---

