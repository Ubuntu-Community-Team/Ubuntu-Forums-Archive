---
title: "No support for device type: power_supply 16.04"
date: 2016-08-09
forum: General Help
---

### Post by badcomputerkarma on 2016-08-09
Hi all
the battery on my brandnew laptop with Ubuntu 16.04 is not being detected.

After some researching in the internet I thought it was an acpi-issue and with a similar problem somebody had success in setting a grub boot parameter to acpi=force. But it didn't work with me.
When I type acpi in the terminal, then I get: 
No support for device type: power_supply

But acpi is installed: #acpi -v gives me
acpi 1.7

Somewhere else a similar problem was called rather a problem of upower ([https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1606159](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1606159)). But as far as I can see there was no solution offered. I have Upower client version 0.99.04

Has anybody an idea how to solve this? Any help is welcome!
Cheers
badcomputerkarma

---

### Post by badcomputerkarma on 2016-10-22
Hello all

In the end I found the answer myself. It was all about the BIOS: The preinstalled BIOS was somehow optimised for Windows. So I found a BIOS by Tuxedo for the same motherboard, optimised for Linux. I changed the BIOS and then everything worked.
Sometimes it's surprising...
Cheers
badcomputerkarma

---

