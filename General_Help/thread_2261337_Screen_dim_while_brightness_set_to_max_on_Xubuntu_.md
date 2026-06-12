---
title: "Screen dim while brightness set to max on Xubuntu 14.04 everytime display turns off"
date: 2015-01-18
forum: General Help
---

### Post by eyal-ez on 2015-01-18
I used to have an issue where every time my laptop would return from suspend, the screen was fully dim (as if brightness was at a minimum) even though the brightness setting was set to maximum - so I had to turn the brightness down by one step and then it would be fine.

Seeking a solution for that issue, I added the following line to /etc/default/grub:
video.use_native_backlight=1
And that seemed to fix it.

 Now (a few weeks later) I'm suddenly experiencing a similar but different issue - again the brightness is at minimum while it is set to maximum, but this time it happens every time my display turns off (due to inacticity) which is more often than the prior issue.

I'm not very knowledgeable on the subject, so I'm not sure if that flag I added did more harm than good.
Any ideas?

---

### Post by eyal-ez on 2015-01-18
These are the values of the brightness settings right after the above reproduction steps:
~ $ cat /sys/class/backlight/intel_backlight/brightness 
842
~ $ cat /sys/class/backlight/intel_backlight/actual_brightness 
842
~ $ cat /sys/class/backlight/intel_backlight/max_brightness 
4882


After turning the brightness down a step and back up so it would return to normal, these are the values:
~ $ cat /sys/class/backlight/intel_backlight/brightness 
842
~ $ cat /sys/class/backlight/intel_backlight/actual_brightness 
3829
~ $ cat /sys/class/backlight/intel_backlight/max_brightness 
4882

---

