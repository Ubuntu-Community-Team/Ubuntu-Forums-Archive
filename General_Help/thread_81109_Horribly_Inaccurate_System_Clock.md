---
title: "Horribly Inaccurate System Clock"
date: 2005-10-23
forum: General Help
---

### Post by ep_ on 2005-10-23
My kernel is 2.6.12-9-k7, (nvidia drivers  installed) and the system clock is horribly inaccurate, it gains about 13 seconds per hour.  As a test, I went into CMOS for a couple of hours and the clock remained accurate.  Leads me to believe the hardware clock is working correctly.  Someone told me this might be a kernel bug. 

I'd like to determine the cause of this problem or what the possilbe solutions might be.  It seems like runing ntp might be overkill.  I just want to be reasonably accurate clock.  I guess I could run ntpdate as  cron job but i'd rather fix the problem.  For example, when an app calls settimeofday I get bumped from FICS (free internet chess server) so there are problems with this as well :(

Solutions?

---

### Post by Korpios on 2005-10-23
Do you have an nforce2 chipset?

[http://kerneltrap.org/node/4872](http://kerneltrap.org/node/4872)

In a nutshell, disable FSB Spread Spectrum in your BIOS.  If that doesn't completely do the trick, you may also need to add "acpi=off" and/or "noapic" to your kernel boot parameters.

---

### Post by ep_ on 2005-10-23
[QUOTE=Korpios]Do you have an nforce2 chipset?

[http://kerneltrap.org/node/4872](http://kerneltrap.org/node/4872)

In a nutshell, disable FSB Spread Spectrum in your BIOS.  If that doesn't completely do the trick, you may also need to add "acpi=off" and/or "noapic" to your kernel boot parameters.[/QUOTE]


Yes I do, specifically the ASUS A7N8X-E MB.  Looks like that did the trick, thank you! More info: [http://www.ussg.iu.edu/hypermail/linux/kernel/0410.1/1505.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0410.1/1505.html)

---

