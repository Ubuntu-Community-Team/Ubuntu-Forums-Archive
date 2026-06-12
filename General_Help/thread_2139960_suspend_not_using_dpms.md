---
title: "suspend not using dpms"
date: 2013-04-28
forum: General Help
---

### Post by psychodn on 2013-04-28
When I put the computer to sleep the monitor STAYS ON, with a blinking cursor (keyboard cursor "_" not a mouse cursor) in the top left.  The screen is all black besides that, but it's an LCD and I would like the screen to be turned off ala xset dpms force off, especially as the backlight keeps me up at night...  Other than that my sleep works flawlessly, I've tried changing several things in /etc/default/acpi-support, but to no avail... I also tried writing an alias that sent xset dpms force off just before the suspend command, but the screen came back on just after, and then also tried an alias with dpms AFTER suspend command, which of course, suspends the processor so it doesn't run until you wake up the system...

---

### Post by gordintoronto on 2013-04-28
Is this a laptop? If so, what brand and model? If the computer is a desktop, what is the brand and model of the monitor?

---

