---
title: "Laptop and CPU frequency"
date: 2016-05-02
forum: General Help
---

### Post by alain.roger on 2016-05-02
Hi,

on my laptop i use Kubuntu 16.04 (upgraded from Kubuntu 15.10).
Everything is ok but i used indicator-cpufreq but it only shows "powersave" and "performance" which is AFAIK normal with newest CPU.

What i do not understand it's that i have the feeling my laptop always runs at the same CPU frequency so around 1GHz while according to "[FONT=monospace][COLOR=#000000]cpupower frequency-info" from 800Mhz to 2.9Ghz.
So basically whatever mode i choose "performance" or "powersave" with indicator-cpufreq, nothing changes.

I mean i use powersave mode while during evening i want to watch a movie or TV on my laptop, so to have a more silent laptop.
During the day, i would like to have my laptop running as fast as it can so around 2.9Ghz.

Is there a way to ensure such state or not ?
in grub i have the command "[/COLOR][/FONT]**intel_pstate=enable"**[FONT=monospace][COLOR=#000000]
[/COLOR][/FONT][FONT=monospace]

Any idea ?
thx.[/FONT]

---

### Post by TheFu on 2016-05-02
Newer processors slow and speed up based on system load.  You want this.  So - if you want the CPU to go fast, give it a non-trivial workload.  That won't include browsing or watching either h.264 or mpeg2 videos. Those are almost always handled inside the GPU, not the CPU.

Common ways to stress a CPU are to calculate Pi to 1,000,000 digits.  Some video transcoding can stress a CPU too.  I see my i7 having thermal issues when doing that for a few hours.  It actually slows down to manage the heat inside the CPU.

```
[325587.658117] mce: [Hardware Error]: Machine check events logged
[332302.688562] CPU1: Core temperature above threshold, cpu clock throttled (total events = 12199068)
[332302.688563] CPU5: Core temperature above threshold, cpu clock throttled (total events = 12199072)
[332302.689565] CPU5: Core temperature/speed normal
[332302.689684] CPU1: Core temperature/speed normal
[332337.900324] mce: [Hardware Error]: Machine check events logged
[332611.540624] CPU0: Core temperature above threshold, cpu clock throttled (total events = 18981083)
[332611.540626] CPU4: Core temperature above threshold, cpu clock throttled (total events = 18981163)
[332611.541631] CPU4: Core temperature/speed normal
[332611.541951] CPU0: Core temperature/speed normal

```  This can be seen using **dmesg**.

You can look in /proc/cpuinfo for the Mhz for each core and the rated speed. Here's an example:
```
thefu@localhost:/tmp$ egrep MHz /proc/cpuinfo
cpu MHz         : 808.500
cpu MHz         : 808.500
cpu MHz         : 808.500
cpu MHz         : 808.500
thefu@localhost:/tmp$ egrep MHz /proc/cpuinfo
cpu MHz         : 2121.000
cpu MHz         : 2121.000
cpu MHz         : 2121.000
cpu MHz         : 2088.187
thefu@localhost:/tmp$ egrep MHz /proc/cpuinfo
cpu MHz         : 1300.687
cpu MHz         : 1366.312
cpu MHz         : 1366.312
cpu MHz         : 1399.125
thefu@localhost:/tmp$ egrep MHz /proc/cpuinfo
cpu MHz         : 1891.312
cpu MHz         : 1563.187
cpu MHz         : 1071.000
cpu MHz         : 1530.375
```
It is a quadcore i3 (2.10GHz peak) ... started some video playback over the network from another box to for X11 to be used. Ran the egrep about 1-2 sec apart.

Sorry - I don't know the GUI way to do this. I didn't have to do anything to enable this behavior.

---

