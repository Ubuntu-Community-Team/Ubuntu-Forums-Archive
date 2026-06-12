---
title: "sysfs permissions after wakeup - how does it work?"
date: 2013-06-17
forum: General Help
---

### Post by truschival on 2013-06-17
Hi group,
I have a laptop i5 with 4 cores running 13.04 (but the problem exists more than some years, was the same on dual-core) 
To show the current frequency I have a plasmoid that accesses information via /sys/devices/cpu/cpuX/cpufreq/cpuinfo_cur_freq

To access this data as humble user I set the permissions in sysfs.conf to:
```

mode devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq = 444
mode devices/system/cpu/cpu2/cpufreq/cpuinfo_cur_freq = 444
```
All works perfect! However, after the system comes up from Suspend-To-RAM (sleep) the situation changed in a strage way:

/sys/devices/system/cpu/cpu**0**/cpufreq/cpuinfo_cur_freq has the desired permission 444
**BUT:**
/sys/devices/system/cpu/cpu**2**/cpufreq/cpuinfo_cur_freq has **400** and a modification date of the time when the system woke up!

Why are they different? 
How sysfs is handled at wakeup? I.e. in which file can I set the permissions? 
Is sysfs.conf the correct location to change permissions in sysfs?

for a long time I have been musing about this annoyance (the fact that I don't understand why). Maybe you can help?

Best Regards
Thomas

---

