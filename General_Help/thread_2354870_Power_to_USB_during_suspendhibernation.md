---
title: "Power to USB during suspend/hibernation"
date: 2017-03-07
forum: General Help
---

### Post by sunbear-c22 on 2017-03-07
I would like to have power from the USB connectors to charge external devices when Ubuntu 16.04 is in suspend/hibernate mode. 
How do I allow this?

I read the following links but did not understand which power state setting actually allow what i want. 
[https://www.kernel.org/doc/Documentation/power/states.txt](https://www.kernel.org/doc/Documentation/power/states.txt)
[https://www.kernel.org/doc/Documentation/power/interface.txt](https://www.kernel.org/doc/Documentation/power/interface.txt)

 By default, power is available for charging when the system is up. No special setting is required. However, there isn't any power in the USB for charging when the system is in suspend or hibernate mode. 

In my BIOS setting, I have  "Charging USB devices in Power State S5" as  "Enabled". However, my USB still do not have power.

---

