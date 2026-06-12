---
title: "Power Saving mode and batteries issue with notebook"
date: 2012-10-18
forum: General Help
---

### Post by adamitj on 2012-10-18
Hi everyone!

I'm using Xubuntu 12.04 in my notebook Sony Vaio. Its setup is an average one, with Intel Core i5 (v1), 8 GB of RAM and a 115 GB SSD drive.

But since I moved from Ubuntu 9.10 I figured out the CPU fan is always at maximum speed. When I run:

```
cat /proc/cpuinfo
```

The CPU voltage is at 800mhz meaning that ACPI probably is working fine. But the battery doesn't lasts more than 1 hour and a half, against ~4 hours of battery life when I was using Ubuntu 9.10.

I'm using Xubuntu because of some GTK apps and other Java apps that doesn't fit well on Unity interface - and because I do not like Unity after all. So I'm missing the point to change power mode on Xubuntu to "Energy Saving" or "Balanced", as it exists on M$ Window$.

Does anyone knows how to handle power modes on Xubuntu? I really liked XFCE and don't want to go back to Unity/Gnome.

---

### Post by LewisTM on 2012-10-18
The Jupiter applet is the best I know for managing power modes. It works fine in Xubuntu.
[http://www.jupiterapplet.org/](http://www.jupiterapplet.org/)

Cheers!

---

