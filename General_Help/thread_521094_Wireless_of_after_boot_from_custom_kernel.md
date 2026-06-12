---
title: "Wireless of after boot from custom kernel"
date: 2007-08-09
forum: General Help
---

### Post by kevinlyfellow on 2007-08-09
I built the latest kernel for my machine and I have a minor problem.  When I boot the machine, my wireless is off by default (ie, I need to press Fn-f2 to turn it on).  Does anyone have any advice on having this on by default when I boot?

Bonus question:  powertop suggests "passing power_save=1 as module parameter" for AC_97 audio.  Where/how do I do this?

---

### Post by DagMan on 2007-08-09
I don't know what module you want for that or where exactly to pass the parameter, but if you can work out what fn F2 does then you can add that action in an init script or add it to one like putting the command as the first thing that runs in gdm or something.  You'd look for it somewhere in /proc/acpi or perhaps somewhere in /sys

That should further confuse things :)

---

### Post by kevinlyfellow on 2007-08-09
> **DagMan said:**
> I don't know what module you want for that or where exactly to pass the parameter, but if you can work out what fn F2 does then you can add that action in an init script or add it to one like putting the command as the first thing that runs in gdm or something.  You'd look for it somewhere in /proc/acpi or perhaps somewhere in /sys

That should further confuse things :)

Yep, it did ;-).  I'm sorry, if it was unclear, the bonus question was independent of the main question (it was there just in case someone stumbled on it, and I didn't feel like it was a big deal at all since I could use other methods instead of 'passing a module parameter' to enable the power saving mode).

---

