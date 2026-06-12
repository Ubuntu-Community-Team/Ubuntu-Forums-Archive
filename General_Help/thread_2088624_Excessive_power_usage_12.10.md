---
title: "Excessive power usage 12.10"
date: 2012-11-27
forum: General Help
---

### Post by rmcd on 2012-11-27
I have a Lenovo x220 that dual boots xubuntu 12.04 and 12.10. Power consumption under 12.04, with wifi off, is about 8 watts according to powertop. The fan exhaust is cool. The laptop gets fantastic battery life, 6-7 hours.

Under 12.10, with the same software running and no wifi, powertop reports over 18-20 watts, the fan runs at high speed with a warm exhaust, and I get lousy battery life, 2-3 hours. 

I have tried 

```

echo Y >sys/module/snd_hda_intel/parameters/power_save_controller
echo 1 > /sys/module/snd_hda_intel/parameters/power_save

```

and I suspended the internal camera with 

```

echo 0 > /sys/bus/usb/devices/1-1.6/power/autosuspend

```

Any thoughts? There are other similar reports, but I have yet to see a solution.

---

### Post by Y^2om&amp;#7sgP on 2012-11-27
Sorry, but I can't offer any constructive help with this.

I tried 12.10 for a while on my laptop, but found so many bugs and crashes that I wiped and reinstalled 12.04

Hope these issues get sorted out before 13.04 arrives

Good luck:)

---

