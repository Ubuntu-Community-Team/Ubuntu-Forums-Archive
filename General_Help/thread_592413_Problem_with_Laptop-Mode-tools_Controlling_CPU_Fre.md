---
title: "Problem with Laptop-Mode-tools Controlling CPU Frequency on Boot"
date: 2007-10-26
forum: General Help
---

### Post by Poilar on 2007-10-26
So, I have an odd situation here:

I have laptop-mode-tools set up so that it runs on boot. I know it's running because "cat /proc/sys/vm/laptop_mode" returns 2.

Laptop-mode seems to recognize that I'm on batteries, because it runs my script I set up to turn on power management for my wireless card. 

Here's the problem:
Laptop-mode-tools does NOT switch the CPU frequency governor on boot. I have in my laptop-tools.conf file the following line:
BATT_CPU_GOVERNOR=conservative

When I unplug my laptop the governor switches appropriates, but booting my computer on batteries does not set the correct governor.

Any ideas?

---

