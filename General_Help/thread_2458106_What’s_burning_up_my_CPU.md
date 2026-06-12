---
title: "What’s burning up my CPU?"
date: 2021-02-16
forum: General Help
---

### Post by W-Unit on 2021-02-16
Running Xubuntu 18.04

According to System Monitor’s “Resources” tab, my CPU usage is 90+%. This is probably accurate, given that everything seems to be running quite slowly. 

According to System Monitor’s “Processes” tab, though, the most CPU-intensive process is using only 25-32% CPU, and if I add up the CPU usage of ALL processes, then I get a total of 40-55%.

So where is the difference coming from? Are there processes that are invisible to System Monitor which are eating up all my CPU power? If so, how do I find these processes?

Thanks for your time.

---

### Post by Frogs Hair on 2021-02-16
Try the following command to display the process.

```
top
```

---

### Post by ajgreeny on 2021-02-16
Run command ```
htop
``` in terminal which may give you more info.  By default mine is set to show the data shows in rows sorted by CPU usage, but there is much more info available in the constantly changing output.
You can change the sort preferences by hitting F6 and clicking on the data by which you wish to sort then hit Enter.

---

### Post by W-Unit on 2021-02-16
Thanks!

Using either top or htop, it looks like the main culprits are VirtualShield.exe (software that I use to connect to a VPN service) - hovering around 8-16% CPU usage while idle (!!) - and chromium-browser, which is sitting around 12-20% CPU usage just for one of its processes (and it has like 6-8 processes) while idle.

While trying to load a page - pretty much any webpage, doesn’t need to be especially complex - chromium’s CPU usage sits above 95% and the entire computer operates slowly nearly to the point of being unusable.

Firefox doesn’t seem to offer any better performance. I don’t think it’s an issue specific to the browser.

This has only been happening for a few days and was never a problem before that. I’m not aware of any major changes or new software installs that could’ve caused this problem to start happening.

Either I figure out why chromium needs 95+% CPU for a full minute in order to load a basic webpage, or I wipe the hard drive and start from scratch I guess. Thanks to anyone who may be able to help me with plan A so I don’t have to resort to plan B.

---

### Post by T6&amp;sfpER35% on 2021-02-16
consider upgrading to 20.04 and see if it still persists?

---

### Post by Doug S on 2021-02-16
> **W-Unit said:**
> VirtualShield.exe (software that I use to connect to a VPN service)
 huh? what do you mean by an ".exe" file? that sound like windows.

CPU load comments by themselves do not mean much without also knowing the CPU frequency, and if has ramped up or not.

what processor make and model? what frequency scaling driver and governor are you using? do you know the temperatures of things? Your issue sounds like it might be some type of throttling, but not sure.

Examples of inquiring as to driver and governor:

```

doug@s18:~$ grep "model name" /proc/cpuinfo
model name      : Intel(R) Core(TM) i5-9600K CPU @ 3.70GHz
model name      : Intel(R) Core(TM) i5-9600K CPU @ 3.70GHz
model name      : Intel(R) Core(TM) i5-9600K CPU @ 3.70GHz
model name      : Intel(R) Core(TM) i5-9600K CPU @ 3.70GHz
model name      : Intel(R) Core(TM) i5-9600K CPU @ 3.70GHz
model name      : Intel(R) Core(TM) i5-9600K CPU @ 3.70GHz
doug@s18:~$ grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu4/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu5/cpufreq/scaling_driver:intel_cpufreq
doug@s18:~$ grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor:schedutil
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor:schedutil

```

---

### Post by dragonfly41 on 2021-02-16
[COLOR=#000000]> huh? what do you mean by an ".exe" file? that sound like windows.

Actually [/COLOR]in Stacer i note that I have running

mono /usr/lib/docky/**Docky.exe**

---

