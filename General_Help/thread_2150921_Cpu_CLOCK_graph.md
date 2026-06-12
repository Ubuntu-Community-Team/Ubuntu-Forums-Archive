---
title: "Cpu CLOCK graph"
date: 2013-06-02
forum: General Help
---

### Post by Juniorr on 2013-06-02
Is there a way I can monitor the CLOCK of my CPU with a graph? Like [http://www.cmg.org/measureit/issues/mit31/m_31_2b.gif](http://www.cmg.org/measureit/issues/mit31/m_31_2b.gif)

That image is just an idea, any graph monitor would be nice, it must record the last hours no matter how much time it's on.

---

### Post by VinDSL on 2013-06-02
My choice is Psensor...

---

### Post by Juniorr on 2013-06-02
Oh, just realised, I need a CPU clock monitor, not a usage one.

---

### Post by pqwoerituytrueiwoq on 2013-06-02
each core functions independently, you can get the current frequencies with 
[FONT=courier new]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq[/FONT]
with the 3.10 kernel on some newer Intel CPUs it is 
[FONT=courier new]cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq[/FONT] (requires root, but you can chmod it to 444 to bypass that)
not sure how to make a graph but that can be used to get the base info, you will probably need the max frequency
[FONT=courier new]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_max_freq[/FONT]
[FONT=courier new]cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_max_freq[/FONT]

divide numbers by 1000 to convert to MHz divide by 1000 again to get GHz

---

### Post by Juniorr on 2013-06-02
Those directories doesn't exist. Just adding to this thread, aside from Jupiter (discontinued), is there a way of setting the cpu frequency to performance? I want to switch to Linux but my frames per second drop on some Valve Source Games, like Team Fortress 2, for example.

---

### Post by pqwoerituytrueiwoq on 2013-06-02
they should exist, one for every core
```
~$ ls /sys/devices/system/cpu/cpu*/cpufreq/
/sys/devices/system/cpu/cpu0/cpufreq/:
affected_cpus     cpuinfo_transition_latency     scaling_governor
bios_limit        related_cpus                   scaling_max_freq
cpb               scaling_available_frequencies  scaling_min_freq
cpuinfo_cur_freq  scaling_available_governors    scaling_setspeed
cpuinfo_max_freq  scaling_cur_freq               stats
cpuinfo_min_freq  scaling_driver

/sys/devices/system/cpu/cpu1/cpufreq/:
affected_cpus     cpuinfo_transition_latency     scaling_governor
bios_limit        related_cpus                   scaling_max_freq
cpb               scaling_available_frequencies  scaling_min_freq
cpuinfo_cur_freq  scaling_available_governors    scaling_setspeed
cpuinfo_max_freq  scaling_cur_freq               stats
cpuinfo_min_freq  scaling_driver

/sys/devices/system/cpu/cpu2/cpufreq/:
affected_cpus     cpuinfo_transition_latency     scaling_governor
bios_limit        related_cpus                   scaling_max_freq
cpb               scaling_available_frequencies  scaling_min_freq
cpuinfo_cur_freq  scaling_available_governors    scaling_setspeed
cpuinfo_max_freq  scaling_cur_freq               stats
cpuinfo_min_freq  scaling_driver

/sys/devices/system/cpu/cpu3/cpufreq/:
affected_cpus     cpuinfo_transition_latency     scaling_governor
bios_limit        related_cpus                   scaling_max_freq
cpb               scaling_available_frequencies  scaling_min_freq
cpuinfo_cur_freq  scaling_available_governors    scaling_setspeed
cpuinfo_max_freq  scaling_cur_freq               stats
cpuinfo_min_freq  scaling_driver
```

in xubuntu i use some genmon applets to control/monitor it
 [[IMG]http://www.zimagez.com/miniature/screenshot-06032013-120215am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-06032013-120215am.php")
[https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin](https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin)
if you call the script like this it should do what you want
[FONT=courier new]sudo cpu-freq-plugin 0 --set[/FONT]
it should be able to set it on any DE

---

### Post by Juniorr on 2013-06-03
Should it be?

---

### Post by pqwoerituytrueiwoq on 2013-06-03
How is you bios configured, for example on a AMD system you would need cool n quiet enabled
overclocking can have the same effect

---

### Post by Doug S on 2013-06-03
If those directories don't exist on your system, then you do not have CPU frequency scaling, either because of a BIOS setting (as pq... mentioned) or because your CPU does not support it. In that case your CPU will already be in "performance" mode.

From an earlier posting:> each core functions independently, you can get the current frequencies with 
[FONT=courier new]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq[/FONT]
with the 3.10 kernel on some newer Intel CPUs it is 
[FONT=courier new]cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq[/FONT]It does not have to be 13.10. And there can be incorrect information displayed as to current CPU frequency for at least some intel CPU's and some motherboards. They actually don't function independently. The only way to know for certain is to use turbostat.

See also [this]("http://ubuntuforums.org/showthread.php?t=2130788&highlight=turbostat") and [this]("http://ubuntuforums.org/showthread.php?t=2063004&highlight=turbostat")

---

### Post by Juniorr on 2013-06-03
I always had Cool and Quiet disabled on my BIOS, now that I enabled it that directory appears.
I'm just not sure how it affects the overall result since I believe the BIOS commands it all.

I also had  "indicator-cpufreq" installed and it falied to load. Now (with QaQ enabled) it loads fine and give's me options to 

Conservative
OnDemand
PowerSave
Performance

Also:

juniorr@juniorr-desktop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq
3000000
3000000
juniorr@juniorr-desktop:~$ cat /sys/devices/system/cpu/cpu?/cpufreq/scaling_governor
performance
performance
juniorr@juniorr-desktop:~$

______________________________________________________________________________________

NOw I jsut have to test if the game will work properly

---

### Post by pqwoerituytrueiwoq on 2013-06-03
> **Doug S said:**
> From an earlier posting:It does not have to be 13.10. And there can be incorrect information displayed as to current CPU frequency for at least some intel CPU's and some motherboards. They actually don't function independently. The only way to know for certain is to use turbostat.was  not referring to ubuntu 13.10 i was referring to linux 3.10, it uses a different scaling driver for some intel CPUs
[FONT=courier new]~$ uname -sr
Linux 3.10.0-031000rc4-generic[/FONT]
[http://www.phoronix.com/scan.php?page=news_item&px=MTI5Mzc](http://www.phoronix.com/scan.php?page=news_item&px=MTI5Mzc)

---

### Post by Doug S on 2013-06-03
> **pqwoerituytrueiwoq said:**
> was  not revering to ubuntu 13.10 i was reffing to linux 3.10, it uses a different scaling driver for some intel CPUsSorry for my misread on that.

---

### Post by Doug S on 2013-06-03
pq...: I tried that kernel you mentioned:```
doug@s15:~/temp$ uname -a
Linux s15 3.10.0-031000rc4-generic #201306020443 SMP Sun Jun 2 08:43:56 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```and it does seem to fix previous possible erroneous entries in "/sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq", but it seems to have other side effects, such as powersave mode not working always but sometimes. I'll play with it some more.

juniorr: sorry for the tangent to your thread.

---

### Post by pqwoerituytrueiwoq on 2013-06-04
i don't recall suggesting anything to you, but i read something about the old ondemand method being less efficient than performance mode was on sandy bridge chips, this new method is more efficient, and according to [FONT=courier new]/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/FONT] the new method is using powersave, but the scaling driver still changes the frequency quite often
there is some stuff about it here
[http://www.phoronix.com/scan.php?page=news_item&px=MTM3NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM3NDQ)
related:
[http://www.phoronix.com/scan.php?page=news_item&px=MTM3NTI](http://www.phoronix.com/scan.php?page=news_item&px=MTM3NTI)

---

### Post by Doug S on 2013-06-04
pq...: You just mentioned the kernel and had a link to the article, so i tried it. I agree you did not recommend it. The new P State driver seems to break several of the previous ways of doing things with respect to frequency scaling. (i.e breaks many of my scripts) Also, I think there are some conflicts between the old ways and the new. Anyway, I don't think the "powersave" and "performance" (the only two that are still there) work the way they used to. To get what used to be "powersave" mode, I had to do this:```
doug@s15:~/temp$ cat set_cpu_powersave_intel_new
#! /bin/bash
echo "1" > /sys/devices/system/cpu/intel_pstate/no_turbo
echo "42" > /sys/devices/system/cpu/intel_pstate/max_perf_pct
```Note: I got "42" from "min_perf_pct", which = 1.6 Ghz / 3.8 Ghz, which is my processors min freq / max turbo freq.```
doug@s15:~/temp$ sudo ./set_cpu_powersave_intel_new
[sudo] password for doug:
doug@s15:~/temp$
```I guess I didn't really need to disable turbo if I was making the min and max clock frequency the same.

---

### Post by pqwoerituytrueiwoq on 2013-06-04
yea it broke my script for monitoring the frequency and changing the govenor that i used with the  xfce4-genmon-plugin package, it was not that hard to fix
i linked to that script earlier, i don't have turbo, but i have two 2.3GHz sandy bridge cores available that i am quite happy with
```
~$ ls /sys/devices/system/cpu/intel_pstate/
max_perf_pct  min_perf_pct  no_turbo
chad@A54C-NB91:~$ cat /sys/devices/system/cpu/intel_pstate/*
100
34
0
```
i think you should split some of ore post into a new thread in ubuntu +1 titled some involving the new intel_pstate scaling driver and testing it

---

### Post by Doug S on 2013-06-04
> **pqwoerituytrueiwoq said:**
> i think you should split some of ore post into a new thread in ubuntu +1 titled some involving the new intel_pstate scaling driver and testing itAgreed. Give me a day or two, and I'll start a thread there.

---

### Post by pqwoerituytrueiwoq on 2013-06-04
yea about that i kinda already did
[CPU Scaling intel_pstate testing (3.10 kernel)](http://ubuntuforums.org/showthread.php?t=2151440&p=12677395#post12677395)

---

### Post by pqwoerituytrueiwoq on 2013-06-06
anyway back on topic, i just made this you will need to install [php5-cli]("apt:php5-cli") to run it
[http://pastebin.com/gvvGYYSV](http://pastebin.com/gvvGYYSV) edit (update): [http://pastebin.com/PYj4wwCj](http://pastebin.com/PYj4wwCj)
[[IMG]http://www.zimagez.com/miniature/screenshot-06062013-031150pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-06062013-031150pm.php")

---

