---
title: "Processor Stepping"
date: 2006-10-31
forum: General Help
---

### Post by bluesmudge on 2006-10-31
Just enabled processor scaling in my bios, its knocked it down from 3ghz to 2.8ghz and often steps back up to 3, but 2.8 is as low as it goes even when idleing . . . does anyone know if theres a reason for that or if there is a limit to how low it'll go?

I have  Intel p4 630 (3ghz, prescott) Emt 64 (but running 32bit edgy) on a Asrock 775vm800 mobo

cheers

Bluesmudge

---

### Post by Jussi Kukkonen on 2006-10-31
Not sure what you mean (stepping usually means a revision number, I'm not sure how those could be enabled), but if it's the same thing as cpu frequency scaling, it's controlled by files in /sys/devices/system/cpu/cpu0/cpufreq/

Goes like this:
```

root@luna:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand
root@luna:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
1000000
root@luna:~# echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
root@luna:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
userspace
root@luna:~# echo 2000000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed
root@luna:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
2000000
root@luna:~# echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
root@luna:~# cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
1000000

```

---

### Post by bluesmudge on 2006-10-31
Sorry funny 5 minutes have editing to scaling!

These files look as if they give me the potential to over clock as well . . . is that correct?

**edit** editing the files doesn't want to work, i suppose because they're in use when i save new changes to their values they just appear the same as they were before!

---

### Post by Jussi Kukkonen on 2006-10-31
not all files are supposed to be edited. You can change  the scaling governor, and once you've set that on 'userspace' you can use scaling_setspeed to select the frequency (as seen in my example).

Look at scaling_available_frequencies and scaling_available_governors to see possible values.

---

### Post by bluesmudge on 2006-10-31
excellent thanks for the help . . . as i suspected my values only go as low as 2800000 seems strange it won't go any lower, but i guess thats life!

---

