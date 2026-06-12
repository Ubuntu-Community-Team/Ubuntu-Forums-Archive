---
title: "How can i limit my processor maximum performance?"
date: 2017-05-27
forum: General Help
---

### Post by Rusz_Tams on 2017-05-27
Hi!
I have a pretty crappy CPU cooling in my setup, and paying for a new cooler does not really worth it, anyways i'm buying a new computer in a while. While i have this one, i'd like to put Ubuntu on it. I already put Ubuntu on it once, but the cooler was very-very loud, and this is a bit annoying, that it is quiet for a minute, after it is very loud for a minute.
I am looking for a menu, which i can find on Windows, and it looks like this:
[http://i.imgur.com/fmDhdhS.png](http://i.imgur.com/fmDhdhS.png) (sorry for the language, but you can recognise it)
Terminal commands are no problems for me, if i could make the computer remember that. So the objective is to set the maximum performance of the processor to 55%, and i'd like the whole system to use this, not only one task or running program. I saw the cpulimit app, but it only limits the performance of the specified program. If my CPU's maximum resource up-pickings are above 55%, fps drops are starting, and so the emergency shutdowns because of overheating.
Thank you for reading.

---

### Post by Doug S on 2017-05-27
The method would depend on which CPU frequency scaling driver and governor you are using. What do you get for these commands:```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

---

### Post by mc4man on 2017-05-27
When I had this Sys76 laptop for an hr. or so before returning due to poor cooling solution, -  to get it to do h.264 encoding without overheating or coming perilously close I remember setting something to 80 or 90% so it would scale back sooner. It didn't overly affect perceived performance but did lower temp while encoding by  15-20C or so.
Don't quite recollect the setting but maybe that's something that could help...

---

