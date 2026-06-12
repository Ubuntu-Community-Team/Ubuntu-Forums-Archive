---
title: "Munin cpuspeed not working after motherboard replacement"
date: 2016-11-05
forum: General Help
---

### Post by cannondale0815 on 2016-11-05
Hey folks!

I had to replace my motherboard on my home-built Ubuntu 16.04 storage server yesterday. Munin was working great beforehand, but now certain modules don't work anymore. For example, if I manually run cpuspeed, I get the following:

```
sudo munin-run cpuspeed
awk: fatal: cannot open file `/sys/devices/system/cpu/cpu0/cpufreq/stats/time_in_state' for reading (No such file or directory)
awk: fatal: cannot open file `/sys/devices/system/cpu/cpu1/cpufreq/stats/time_in_state' for reading (No such file or directory)
awk: fatal: cannot open file `/sys/devices/system/cpu/cpu2/cpufreq/stats/time_in_state' for reading (No such file or directory)
awk: fatal: cannot open file `/sys/devices/system/cpu/cpu3/cpufreq/stats/time_in_state' for reading (No such file or directory)
awk: fatal: cannot open file `/sys/devices/system/cpu/cpu4/cpufreq/stats/time_in_state' for reading (No such file or directory)
awk: fatal: cannot open file `/sys/devices/system/cpu/cpu5/cpufreq/stats/time_in_state' for reading (No such file or directory)
awk: fatal: cannot open file `/sys/devices/system/cpu/cpu6/cpufreq/stats/time_in_state' for reading (No such file or directory)
awk: fatal: cannot open file `/sys/devices/system/cpu/cpu7/cpufreq/stats/time_in_state' for reading (No such file or directory)
```

I removed and reinstalled munin, munin-node and the munin plugins (extra and core) to no avail. I'm sure it's something simple, but it's been such a long time that I've touched the munin configuration that I'm a bit at a loss.

Thanks!
-J

P.S.: I have an Intel Xeon E3 processor sitting on a Supermicro board with c202 chipset

---

### Post by cannondale0815 on 2016-11-05
Nevermind. It started working all by itself several hours later. Weird.

---

