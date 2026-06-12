---
title: "Battery monitor not synchronized with battery"
date: 2014-08-10
forum: General Help
---

### Post by Asaltu on 2014-08-10
I recently notice that my battery monitor is not correctly synchronized with my battery. I don't know for how long this has been going on, but there are two occurrences where this behavior could have happened:
[LIST]
[*]After upgrading to Trusty
[*]After start of use of new battery with higher capacity
[/LIST]
The second point happened already *before* upgrading.

Basically, what happens is that the battery monitor shows the battery discharging, down to 2%, which I set as critical level. This takes about 2 hours of "regular" computer work. But after reaching 2% (virtually), I can still use my computer for another 2 or 3 hours, and the monitor will "hang" at 2% till the battery dies, without any prior warning when reaching the ACTUAL critical level.

What could have caused this? How can I solve this?

Thanks in advance for your help!

---

### Post by tgalati4 on 2014-08-10
The battery monitor has a learning algorithm.  It gets more accurate over time.  Unfortunately, you need to reset it with a new battery and you need several charge-discharge cycles for it to learn what the real capacity is.  This can cause you to lose work if your battery is old, weak, or if the BIOS doesn't provide a clean shutdown on low voltage.  I would initially set a conservative "Go to Sleep at 20%" and then after 10 full charge/discharge cycles, gradually lower the threshold to 18%, 15%, 13%, 10%.  I would not go below 10% but that is your choice.

I don't use Kubuntu, so you will have to search for how to reset it in KDE.

---

### Post by Asaltu on 2014-08-10
Thanks for your feedback tgalati4

Since I have the battery, it has completely discharged for more than 20 times. That should be enough for calibration I would say.

upower --dump tells me  energy-full-design:  17.686 Wh
My battery is 14.8V and 5200mAh, which should sum up to about 76 Wh instead, if I am not mistaken.

Anyone has any thoughts on how to "force" a reset on the battery monitor, or how to manually calibrate? (or any other though that might help...)

---

### Post by Asaltu on 2014-08-12
Anyone?

---

