---
title: "Ubuntu 18.04.2 constantly freezing"
date: 2019-06-08
forum: General Help
---

### Post by aquasome on 2019-06-08
My PC is constantly freezing multiple times every 10-20 minutes and the only way to continue using it is to reboot the PC, but only to have it freeze again a a few minutes. Strangely I can still hear sound coming from the PC. When I open the logs, I always get the messages,"AMD-Vi: Unable to write to IOMMU perf counter." and "ACPI BIOS Error (bug): Failure creating [\_SB.SMIB], AE_ALREADY_EXISTS (20180531/dsfield-594)" or something similar to the last one. Any help is appreciated, I am new to Linux and am trying to resolve this frustrating issue

CPU: Ryzen 2200G
GPU: Integrated Vega 8 GPU

---

### Post by Autodave on 2019-06-08
How long ago did this problem start: was it right after you installed Linux?

Please give us some specs on your equipment and what version you installed.

---

### Post by aquasome on 2019-06-08
I&#8217;ve installed Ubuntu about a month ago, this problem has been always occurring but is happing a lot recently. My specs are a Ryzen 2200G and I am currently using the integrated Vega 8 GPU

---

### Post by pbwolf on 2019-06-08
The grub boot menu might offer a multi-hour test of memory and such.  If the computer freezes when running that kind of test, it would affirm that the problem is really with the hardware, not Ubuntu.  I've seen freezes result from a loose memory module or unclean electric power.  If the computer is not plugged into a UPS, try that.  If it's still erratic, you might be able to restore it to good working order by popping the case open and re-seating some components.

---

