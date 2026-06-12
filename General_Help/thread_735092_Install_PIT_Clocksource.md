---
title: "Install PIT Clocksource"
date: 2008-03-25
forum: General Help
---

### Post by spinez on 2008-03-25
I am having all sorts of time-sync problems with windowsxp running as a guest in vmware server.  I have been researching the issue and many things point to using clocksource=pit in your kernel paramaters  However, it appears that the pit clocksource is not available on my system (7.10 i386).  Is there a way I can make the pit clocksource available?

[ksteely@spinezlap ~]: sudo cat /sys/devices/system/clocksource/clocksource0/available_clocksource 

hpet acpi_pm jiffies tsc

---

