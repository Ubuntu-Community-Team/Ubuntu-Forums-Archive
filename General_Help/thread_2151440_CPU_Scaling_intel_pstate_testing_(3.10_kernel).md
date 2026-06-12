---
title: "CPU Scaling intel_pstate testing (3.10 kernel)"
date: 2013-06-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-06-04
This is not for AMD CPUs just so you know

Info:
[http://www.phoronix.com/scan.php?page=news_item&px=MTM3NDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTM3NDQ)

XFCE users may be interested in [this script]("https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin") for the [genmon applet]("apt:xfce4-genmon-plugin"), the icons are [here]("http://www.mediafire.com/download/ef6ghr6xxg656vc/icons.tar.gz") (icons are from the gnome2 sensors/cpu freq applets)

Do determine if your CPU uses the new [FONT=courier new]intel_pstate[/FONT] driver, you will need the 3.10 kernel, then run this
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
```
You will get 1 line for every core/thread your CPU has, it is gives you [FONT=courier new]intel_pstate[/FONT] you can try it out
I have been watching my core frequencies on my laptop, so far I have found 67 speeds it will use, which is way more than it used under the old method of cpu scaling

I have written a [PHP script]("http://pastebin.com/QdhQ7QwQ") to find frequencies (requires that [php5-cli]("apt:php5-cli") be installed)
On line 3 you can fill out known speeds like this [[IMG]http://www.zimagez.com/miniature/screenshot-06042013-124556pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-06042013-124556pm.php")
On line 6 you can change the number 60 to make it search for more or less time, the script uses a brute force method to find frequencies so more time will have more results
You will need to add read access to this, by default only root can read it
[FONT=courier new]sudo chmod 444 /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq[/FONT]

I also made [another script]("http://pastebin.com/PYj4wwCj") to track the cpu frequency

On my laptop my 67 known speeds are```

 782 Mhz as  34%
 805 Mhz as  35%
 828 Mhz as  36%
 851 Mhz as  37%
 874 Mhz as  38%
 897 Mhz as  39%
 920 Mhz as  40%
 943 Mhz as  41%
 966 Mhz as  42%
 989 Mhz as  43%
1012 Mhz as  44%
1035 Mhz as  45%
1058 Mhz as  46%
1081 Mhz as  47%
1104 Mhz as  48%
1127 Mhz as  49%
1150 Mhz as  50%
1173 Mhz as  51%
1196 Mhz as  52%
1219 Mhz as  53%
1242 Mhz as  54%
1265 Mhz as  55%
1288 Mhz as  56%
1311 Mhz as  57%
1334 Mhz as  58%
1357 Mhz as  59%
1380 Mhz as  60%
1403 Mhz as  61%
1426 Mhz as  62%
1449 Mhz as  63%
1472 Mhz as  64%
1495 Mhz as  65%
1518 Mhz as  66%
1541 Mhz as  67%
1564 Mhz as  68%
1587 Mhz as  69%
1610 Mhz as  70%
1633 Mhz as  71%
1656 Mhz as  72%
1679 Mhz as  73%
1702 Mhz as  74%
1725 Mhz as  75%
1748 Mhz as  76%
1771 Mhz as  77%
1794 Mhz as  78%
1817 Mhz as  79%
1840 Mhz as  80%
1863 Mhz as  81%
1886 Mhz as  82%
1909 Mhz as  83%
1932 Mhz as  84%
1955 Mhz as  85%
1978 Mhz as  86%
2001 Mhz as  87%
2024 Mhz as  88%
2047 Mhz as  89%
2070 Mhz as  90%
2093 Mhz as  91%
2116 Mhz as  92%
2139 Mhz as  93%
2162 Mhz as  94%
2185 Mhz as  95%
2208 Mhz as  96%
2231 Mhz as  97%
2254 Mhz as  98%
2277 Mhz as  99%
2300 Mhz as 100%
```
the strange thing is my 1st speed, if I run [FONT=courier new]cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_min_freq[/FONT] I should get the lowest possible frequency the system will use which is 800 MHz, however the system has been seen running at 782 MHz
I actually just noticed the CPU seems to run at every percentage point, thanks to the sorted data. The script does round the percentages, but I turned rounding off and they are all exact values
I am unable to test turbo core stuff as I don't have any hardware that can do that, i would like to know if the [FONT=Courier New]cpuinfo_cur_freq[/FONT] files shows turbo

---

### Post by Doug S on 2013-06-04
> **pqwoerituytrueiwoq said:**
> I am unable to test turbo core stuff as I don't have any hardware that can do that, i would like to know if the [FONT=Courier New]cpuinfo_cur_freq[/FONT] files shows turboIt does show the actual turbo frequencies and is now never different that the results of```
grep MHz /proc/cpuinfo
```at least that I have seen so far. In this example my system is 3.4 GHz with turbo up to 3.8 GHz, and I have CPU 7 fully loaded:```
doug@s15:~/temp$ grep MHz /proc/cpuinfo
cpu MHz         : 3672.000
cpu MHz         : 3672.000
cpu MHz         : 3672.000
cpu MHz         : 3774.000
cpu MHz         : 3672.000
cpu MHz         : 3672.000
cpu MHz         : 3672.000
cpu MHz         : 3774.000
doug@s15:~/temp$ sudo cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq
3672000
3638000
3672000
3774000
3672000
3672000
3604000
3774000
```(slight differences because of time delay between commands. It is CPU 7 that matters for this example.)

 With turbo turned off, I get many CPU frequencies, but not one for every percent setting, with turbo turned on, I seem to get less frequencies. Also, I am finding some weird things with this new frequency scaling stuff, and it isn't backwards compatible with how things were. I need some time (a day or two) to make a better and more compete posting here, as there are tests I didn't get to yet.

Other readers: pq...q and I were on [another thread]("http://ubuntuforums.org/showthread.php?t=2150921") and went off on a tangent about this. It was decided to start a new thread here.

---

### Post by pqwoerituytrueiwoq on 2013-06-04
did you try my php script to find frequencies, i set the loop to 500 (line 6) and went and did stuff, that should find most of your speeds
nice to know that my genmon plugin supports turbo core on this new driver
i am supried you can have turbo running on 8 threads at the same time, i thought it had to downclock 1 or more cores to up the clock on another core, could be a bug in the driver

---

### Post by Doug S on 2013-06-05
> **pqwoerituytrueiwoq said:**
> did you try my php script to find frequencies, i set the loop to 500 (line 6) and went and did stuff, that should find most of your speedsNo I didn't. I already had a way of doing it, so continued with my method. I'll have a look at your method later on.> I am supried you can have turbo running on 8 threads at the same time, i  thought it had to downclock 1 or more cores to up the clock on another  core, could be a bug in the driverI only had one CPU fully loaded, and I actually never see my non-idle CPU's at different actual frequencies. If I fully load all 8 of my CPU's, the frequency does drop a little:```
New P-state driver - all CPU's loaded (governor = PERFORMANCE)
doug@s15:~/temp$ grep MHz /proc/cpuinfo
cpu MHz         : 3468.000
cpu MHz         : 3468.000
cpu MHz         : 3468.000
cpu MHz         : 3468.000
cpu MHz         : 3468.000
cpu MHz         : 3468.000
cpu MHz         : 3468.000
cpu MHz         : 3468.000

Old p_state driver - all CPU's loaded (turbostat is the only way to know the actual frequency)
doug@s15:~/temp$ sudo ./turbostat
 cr CPU    %c0  GHz  TSC    %c1    %c3    %c6    %c7  %pc2  %pc3  %pc6  %pc7
         100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   0   0 100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   0   4 100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   1   1 100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   1   5 100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   2   2 100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   2   6 100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   3   3 100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   3   7 100.00 3.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
```Edit: The New P-state driver all CPUs loaded example above was for PERFORMACE governor. Below is for POWERSAVE governor.```
doug@s15:~/temp$ grep MHz /proc/cpuinfo
cpu MHz         : 1768.000
cpu MHz         : 1768.000
cpu MHz         : 1768.000
cpu MHz         : 1768.000
cpu MHz         : 1768.000
cpu MHz         : 1768.000
cpu MHz         : 1768.000
cpu MHz         : 1768.000
```Edit 2: But that is inconsistent, as I did it again adding 1 CPU 100% load at a time, and ended up at a different clock frequency for all 8 CPUs loaded:
1 CPU 100% loaded, Frequency: 3.774 GHz
2 CPUs 100% loaded, Frequency: 3.570 GHz
3 CPUs 100% loaded, Frequency: 3.570 GHz
4 CPUs 100% loaded, Frequency: 3.468 GHz
5 CPUs 100% loaded, Frequency: 3.468 GHz
6 CPUs 100% loaded, Frequency: 3.468 GHz
7 CPUs 100% loaded, Frequency: 3.468 GHz
8 CPUs 100% loaded, Frequency: 3.468 GHz

Edit: Adding what "turbostat -v" says for max Vs. cores used:```
doug@s15:~/temp$ [COLOR=#ff0000]sudo ./turbostat -v[/COLOR]
GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
16 * 100 = 1600 MHz max efficiency
34 * 100 = 3400 MHz TSC frequency
35 * 100 = 3500 MHz max turbo 4 active cores
36 * 100 = 3600 MHz max turbo 3 active cores
37 * 100 = 3700 MHz max turbo 2 active cores
38 * 100 = 3800 MHz max turbo 1 active cores
```

---

### Post by Doug S on 2013-06-05
The current, or "old" frequency scaling driver for intel stuff has issues and sometimes gives false information, so when pq...q mentioned there was a new p-state driver in the 3.10 series kernel I wanted to have a test drive.

Summary: There are issues.

My system: i7 @ 3.4 GHz with turbo to 3.8 GHz and a minimum frequency of 1.6 GHz (42% of 3.8 GHz. The new driver uses percents.)

Experiment: Set powersave mode on all CPUs: Other stuff = default

What used to happen: All CPU's would always be at 1.6 GHz.

What happens now:

Load CPU 7: (taskset -c 7 ./testtme): (testtme is a simple CPU loading program that actually does nothing.)
Sometimes it will go immediately to 3.774 GHz
Sometimes it will go to 3.774 GHz after a few seconds
Sometimes it will go to 1.768 Ghz and stay there (tested to 426 seconds duration).

Similar results for other CPUs.

Now: turn off turbo
Sometimes it will go immediately to 3.40 GHz
Sometimes it will go to 3.40 GHz after a few seconds
Sometimes it will go to 1.768 Ghz and stay there (tested to 260 seconds duration) (rate is about 1 in 10 to 1 in 20 times)

Experiment: Set performance mode on all CPUs: Other stuff = default

Loaded CPU will go immediately to 3.774 GHz

Now: turn off turbo
Sometimes loaded CPU will go to 1.768 GHz and stay there. (tested for 25 seconds duration).
Mostly it will go to 3.4 GHz.

Experiment: How many frequencies are used?
Method: set the min and max percent frequencies to the same value.
See attached graphs, for both reported frequencies and as calculated (sanity check).

Why the large jump in frequencies? Do they not work for some reason?
Boot back to an older kernel (old driver), the list of available frequencies is:```
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
```And so I tried each of the available frequencies that were bypassed by the new driver, namely 1.9, 2.0, 2.1, 2.2, 2.4, and 2.5 GHz. I used the userspace governor. All the frequencies worked fine: Example:```
doug@s15:~/temp$ cat set_cpu_userspace
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "userspace" > $file; done

for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_setspeed; do echo "2500000" > $file; done

cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

grep MHz /proc/cpuinfo


``````
doug@s15:~/temp$ sudo ./turbostat
 cr CPU    %c0  GHz  TSC    %c1    %c3    %c6    %c7  %pc2  %pc3  %pc6  %pc7
          12.52 2.51 3.41  19.83   0.00  67.66   0.00  0.00  0.00  0.00  0.00
   0   0   0.02 2.51 3.41   0.65   0.00  99.33   0.00  0.00  0.00  0.00  0.00
   0   4   0.05 2.51 3.41   0.62   0.00  99.33   0.00  0.00  0.00  0.00  0.00
   1   1   0.02 2.51 3.41  15.46   0.00  84.52   0.00  0.00  0.00  0.00  0.00
   1   5   0.00 2.51 3.41  15.48   0.00  84.52   0.00  0.00  0.00  0.00  0.00
   2   2   0.01 2.51 3.41  13.20   0.00  86.79   0.00  0.00  0.00  0.00  0.00
   2   6   0.00 2.50 3.41  13.21   0.00  86.79   0.00  0.00  0.00  0.00  0.00
   3   3   0.01 2.51 3.41  99.99   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   3   7 100.00 2.51 3.41   0.00   0.00   0.00   0.00  0.00  0.00  0.00  0.00
```

Edit: The original graphs (one now replaced) were done with increasing percent requested frequencies. New tests were done with decreasing percent requested frequencies, and then the big gap in frequencies was not present.

---

### Post by Doug S on 2013-06-05
Results on my computer (governor = POWERSAVE; tubo on) using pq...q's php script:```
Total found: 50
Sorted data:
1598 Mhz as  42%
1632 Mhz as  43%
1666 Mhz as  44%
1700 Mhz as  45%
1734 Mhz as  46%
1768 Mhz as  47%
1802 Mhz as  47%
1836 Mhz as  48%
1870 Mhz as  49%
1904 Mhz as  50%
1938 Mhz as  51%
1972 Mhz as  52%
2006 Mhz as  53%
2040 Mhz as  54%
2074 Mhz as  55%
2108 Mhz as  55%
2142 Mhz as  56%
2176 Mhz as  57%
2210 Mhz as  58%
2244 Mhz as  59%
2278 Mhz as  60%
2312 Mhz as  61%
2346 Mhz as  62%
2380 Mhz as  63%
2414 Mhz as  64%
2448 Mhz as  64%
2516 Mhz as  66%
2550 Mhz as  67%
2618 Mhz as  69%
2686 Mhz as  71%
2856 Mhz as  75%
2924 Mhz as  77%
2992 Mhz as  79%
3060 Mhz as  81%
3094 Mhz as  81%
3162 Mhz as  83%
3196 Mhz as  84%
3230 Mhz as  85%
3366 Mhz as  89%
3400 Mhz as  89%
3468 Mhz as  91%
3502 Mhz as  92%
3536 Mhz as  93%
3570 Mhz as  94%
3604 Mhz as  95%
3638 Mhz as  96%
3672 Mhz as  97%
3706 Mhz as  98%
3740 Mhz as  98%
3774 Mhz as  99%
```Why so different than what I found? It includes all CPU states, including idle and such in between. I was only using active CPU (in the c0 state, I think it is called) information and was trying to specifically set CPU frequencies. There is work that I do, where I must know that I can "lock" the CPU frequency at some value.

---

### Post by pqwoerituytrueiwoq on 2013-06-05
I am sure there are more than just those
can you post the output of this
[FONT=courier new]cat /sys/devices/system/cpu/cpu*/cpufreq/{scaling_max_freq,cpuinfo_max_freq}[/FONT]
you don't have the max freq i would expect (3.4GHz)
your turbo core speed seems to be the norm maxi expected to see something like
3774 MHz as 130%

---

### Post by Doug S on 2013-06-05
```
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/{scaling_max_freq,cpuinfo_max_freq}
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
3800000
```With turbo enabled 100% = 3.8 GHz. With turbo disabled 100% = 3.4 GHz (see also my graphs in previous post)

---

### Post by pqwoerituytrueiwoq on 2013-06-06
I did some more testing, the CPU cores seem to run at the same speed as the other cores, can you confirm this (i only have 2 cores)
there is a new script in post 1 and in the thread you linked in your 1st post

a couple times they are not the same in the chart, but the script runs leaner so it can't get both core's current speed at the same nanosecond second, it is way too close to be coincidence

If your system does the same with turbo on file a bug report, there is no way that is the correct behavior for it,if they are the same with turbo when over 3.4Ghz that is overclocking not turbo

---

### Post by Doug S on 2013-06-06
> **pqwoerituytrueiwoq said:**
> I did some more testing, the CPU cores seem to run at the same speed as the other cores, can you confirm this (i only have 2 cores)Yes, for any CPU in the C0 state, the frequency is always the same. This was an issue with the previous frequency scaling driver, as it gave the impression that different CPU's were at different speeds when in fact they were not. When a CPU is not in the C0 state, then, myself, I don't care what is listed for frequency.> If your system does the same with turbo on file a bug report, there is no way that is the correct behavior for it,if they are the same with turbo when over 3.4Ghz that is overclocking not turboI disagree. Both the old scaling driver and the new one are, if not the same, at least similar in this regard, and as far I a have seen obey the re-rating rules as per the output from "turbostat -v" that I added a few hours ago to the end of my post #4 above.

Now, for my post #5 above, I wrote things like "sometimes I get this" and "sometimes get that". I wanted to get a better value for the actual probability that the CPU will not step up to the frequency it should get to.

With turbo off and POWERSAVE governor, 1020 times I launched a 100% CPU loading task on CPU 7 and then asked for the CPU frequency after 5 seconds; 222 times it was 1.768 GHz; once it was 2.788 GHz; 307 times it was 3.366 GHz; and 490 times it was 3.4 GHz. I think, with no proof, 3.366 and 3.4 are the same within some noise or whatever. So the probability that it doesn't step up properly is about 22%. I'll do some other scenarios, but this test take 5 hours. This, I think, is a bug. Does anyone else see this issue? It might be more probable for me, as I run ubuntu server and not desktop, so all of my CPU's are more likely to be idle at the start of the each sample loop than ubuntu desktop CPUs.

I did the same as the above test, but 1000 times and not specifying a CPU. The CPU frequency did not ramp up many times. Exact numbers are not known, because I did not know which CPU frequency to measure.

Turbo = on; governor = POWERSAVE; Samples 672; In 19.9% of samples, the CPU did not step up.
Data: Samples 672; 134 samples were 1.768 GHz; 1 sample was 2.176 GHz; 277 samples were 3.672 GHz (meaning another core was doing something); 2 samples were 3.740 GHz; 253 samples were 3.774 GHz.

Turbo on; governor = PERFORMANCE; Samples 1000; In 0 % of samples, the CPU did not step up.
Data: Samples 1000; 13 samples were 3.57 GHz (meaning two other cores were doing something); 524 samples were 3.672 GHz (meaning another core was doing something); 5 samples were 3.74 GHz; 458 samples were 3.774 GHz.

---

### Post by Doug S on 2013-06-08
For the tests that gave the attached graphs in post #5 above, the one CPU (7 in that case) was always 100% loaded for the entire experiment.
Basically the same test was done again, but: The requested frequency was ramped up and down 12 times (Why 12? because I had meant to do 10, but forgot to increment the loop counter and discovered it after 12 cycles); The CPU (7 in this case) returned to idle between each data sample.
The results are attached as graphs.

---

### Post by pqwoerituytrueiwoq on 2013-06-10
Frequencies no longer appear the to synchronized in 3.10rc5

---

### Post by Doug S on 2013-06-10
I tested the mainline 3.10rc5 (not the ubuntu one, the kernel.org one) yesterday and found it to be the same as before. I also did not observe any change log notes related to the pstate driver.

By the way, I filed a bugzilla report: [https://bugzilla.kernel.org/show_bug.cgi?id=59481](https://bugzilla.kernel.org/show_bug.cgi?id=59481) (still need to add notes from last nights test)

I did not actually look at your charts yet, I'll have to do that later.

---

### Post by pqwoerituytrueiwoq on 2013-06-10
The charts are just html files that use google charts, should open on any device that can extract the archive
i am using the mainline Ubuntu kernel

---

### Post by dino99 on 2013-06-10
Looking that thread, i'm trying to grab data from a q9550; but it looks like the kernel driver does not load cpufreq here (missing from /sys/devices/....)
What could be wrong with that module ? (its a genuine 13.10 install)

---

### Post by Doug S on 2013-06-10
> **dino99 said:**
> Looking that thread, i'm trying to grab data from a q9550; but it looks like the kernel driver does not load cpufreq here (missing from /sys/devices/....)
What could be wrong with that module ? (its a genuine 13.10 install)My quess is that the new intel pstate driver does not support your CPU yet. It is very limited so far, I think only "sandy bridge" processors, with more to be added later (and I did not check about your CPU type. if it should be using the new driver or not). The way to tell is to do this:```
doug@s15:~$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
```Edit: Adding: If your system does not have any CPU frequency scaling at all you will get this:```
doug@doug-64:~$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver: No such file or directory
```

---

### Post by dino99 on 2013-06-11
> **Doug S said:**
> Edit: Adding: If your system does not have any CPU frequency scaling at all you will get this:```
doug@doug-64:~$ [COLOR=#ff0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver: No such file or directory
```

Thanks Doug for the clarification

The q9550 cpu supports dynamic frequency scaling, but the kernel is broken since acpi_cpufreq is builtin (aka since 9.10 ) for that chipset:

w83627ehf: Found W83667HG chip at 0x290 
ACPI: I/O resource w83627ehf [0x295-0x296] conflicts with ACPI region HWRE [0x290-0x299] 
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

Looks like the kernel team will never fix that issue. ;);)

---

### Post by Doug S on 2013-06-11
@pq...q: I finally got around to trying your script. Very nice. The only thing I would suggest to change is the legend, as my computer has only 4 cores, but 2 CPUs per core, for 8 CPUs. I would also number them from 0 to 7 to match other ways of inquiring as to frequency. A couple of examples attached. In one I compiled the Ubuntu serverguide, both html and pdf, during the script run. In the other I was running 4 processes at a load of 0.18 and a sleep frequency of 52 Hertz per process.

---

### Post by pqwoerituytrueiwoq on 2013-06-11
The core numbers starting at 1 is a feature, to convert it to the number you are looking for take the core number and subtract 1
it does have options use -h or --help to get them
i don't know a way to see the difference between a core and a thread, you can click a label in the legend to set a outline around that line

---

### Post by pqwoerituytrueiwoq on 2013-06-11
on wake from suspend the frequencies appear synchronized, anyone able to confirm

---

### Post by Doug S on 2013-07-03
> **pqwoerituytrueiwoq said:**
> on wake from suspend the frequencies appear synchronized, anyone able to confirmI suspect that when coming out of suspend there is a fair bit of stuff to do. So it should not be a surprise that the frequencies appear synchronized, as all CPUs that are in the C0 state (not idle) will be at the same frequency.

See also the "[Intel 2nd gen core desktop vol 1 datasheet]("http://www.intel.com/content/www/us/en/processors/core/2nd-gen-core-desktop-vol-1-datasheet.html")" - Chapter 4 Power Management - Section 4.2 Processor Core Power Management - Sub-section 1 Enhanced Intel SpeedStep Technology - Bullet point 2 - 3rd sub-list entry (page 46 of the html or pdf):> All active processor cores share the same frequency and voltage. In a multicore processor, the highest frequency P-state requested amongst all active cores is selected.By the way, there has been significant activity on the [bugzilla]("https://bugzilla.kernel.org/show_bug.cgi?id=59481") report mentioned previously.

---

### Post by pqwoerituytrueiwoq on 2013-07-10
Looks like a solution for my frequencies after suspend being synced has been found
even fixed a display issue on my intel gpu that sowed up after suspend
[https://bugzilla.kernel.org/show_bug.cgi?id=59781](https://bugzilla.kernel.org/show_bug.cgi?id=59781)

---

### Post by Doug S on 2013-07-10
pq...q: Oh, I didn't understand your after suspend problem. I thought they were only temporarily synchronized. And thanks for the link to the interesting bug report.

---

### Post by JMB74 on 2013-07-14
pstate scaling disabled by default in the ubuntu kernel builds for now it seems?

[https://launchpad.net/ubuntu/saucy/+source/linux/3.10.0-2.11](https://launchpad.net/ubuntu/saucy/+source/linux/3.10.0-2.11)

> * SAUCE: intel_pstate -- toggle default to disable

ref bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188647](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188647)

---

### Post by Doug S on 2013-07-14
> **JMB74 said:**
> pstate scaling disabled by default in the ubuntu kernel builds for now it seems?

[https://launchpad.net/ubuntu/saucy/+source/linux/3.10.0-2.11](https://launchpad.net/ubuntu/saucy/+source/linux/3.10.0-2.11)

ref bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188647](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188647)Thanks for the links. That is probably a good thing. In my opinion, it was premature to make it the default cpu scaling driver (for certain intel CPU's), as it clearly has issues. However, they are quite responsive in working towards resolving the issues. Ultimately, it should be a superior driver.

---

### Post by Doug S on 2013-08-05
Kernel 3.11RC4 contains changes to intel_pstate.c that fix the issue of sometimes (about 25% of the time) failing to respond to a load change.

---

### Post by pqwoerituytrueiwoq on 2013-08-06
but it still does not preserve permissions on my cpuinfo_cur_freq file across suspend, expet on my 1st core

---

### Post by Linuxisfast on 2013-09-30
Pstate scaling combined with Intel Thermal Daemon works brilliant. In fact now for the first time the laptop temps match or better Windows 8. Also the Pstate utilizes CPU, especially multicore ones like i7 far better than ondemand. Its also more efficient, along with less temperature, combined with TLP, battery life is far better. This is my experience on Arch so I suggest pstate be turned on and Intel Thermal Daemon be put in the repository. Also the daemon prevents high temperature and shut downs during peak load as it monitors and scales the CPU far better than just the stand alone cpu-freq and bios and acpi method of power management.

All this has been tested on three laptops, one ASUS K53M with i5 SB, ASUS K66-VM with i7IVB and ASUS UX51.

---

### Post by davidbaumann2 on 2013-10-01
So on 13.10, what's the easy way to enable?

---

### Post by pqwoerituytrueiwoq on 2013-10-01
> **davidbaumann2 said:**
> So on 13.10, what's the easy way to enable?
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver
```
if it says intel_pstate it is already enabled and working, if not try the [mainline kernel](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

---

### Post by Doug S on 2013-10-01
Based on [some bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188647") (which should be reversed, at this point), I think that on Ubuntu the intel pstate driver might be disabled by default.
You can test using the method pq...q mentioned.
You can enable it via "intel_pstate=enable" in /etc/default/grub. Example (where I also disable IPV6):```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 intel_pstate=enable"
```If you modify the grub file then you have to```
sudo update-grub
```to update the actual loader on disk. Then re-boot

---

### Post by mc4man on 2013-10-01
> **Doug S said:**
> Based on [some bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188647") (which should be reversed, at this point), I think that on Ubuntu the intel pstate driver might be disabled by default.

I see people commenting in that bug recently about about re-enabling intel_pstate again by default. 
It may be more effective to start a new report requesting this than commenting in a 'fix-released' report

---

### Post by davidbaumann on 2013-10-01
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver acpi-cpufreq

```

This now on my Vaio Pro Haswell, and the same on my I7 3rd Generation Laptop.

David.

---

### Post by Linuxisfast on 2013-10-01
Along with Pstate we need the excellent Intel Thermal Daemon in ppa or software center. Currently it has to be compiled into Ubuntu. The temperature management now is better with this than in Windows. With TLP the battery life too is same as Windows if using kernel 3.11

---

### Post by Linuxisfast on 2013-10-01
> **davidbaumann said:**
> ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver acpi-cpufreq

```

This now on my Vaio Pro Haswell, and the same on my I7 3rd Generation Laptop.

David.


Which version of Ubuntu do you get this?

---

### Post by davidbaumann on 2013-10-02
Hello,

I am sorry I can't do uname -r here.
It's both Kubuntu 13.10 x64 with Kernel 3.11.0.8 (default).

I don't have this daemon running, only intel_pstate=enable in grub.

David.

---

### Post by Linuxisfast on 2013-10-02
> **davidbaumann said:**
> Hello,

I am sorry I can't do uname -r here.
It's both Kubuntu 13.10 x64 with Kernel 3.11.0.8 (default).

I don't have this daemon running, only intel_pstate=enable in grub.

David.


This indicates that pstate is turned off by default in the Ubuntu kernel.

---

### Post by shuhao on 2013-10-20
Does the Intel Thermal Daemon control fans? Do I need thinkfan running after installing that?

---

### Post by pqwoerituytrueiwoq on 2013-10-21
i think the bios controls fan speed by default

---

### Post by Linuxisfast on 2013-10-23
> **shuhao said:**
> Does the Intel Thermal Daemon control fans? Do I need thinkfan running after installing that?


It controls the temperature, as mentioned the BIOS controls the fans. So if your temp is low for the BIOS threshold, its off. There is an utility called Thinkfan to control fans on Thinkpad.

---

### Post by mörgæs on 2013-10-23
Moved to General Help, as 13.10 is now an official release.

---

### Post by pnarciso on 2013-10-23
I'm running ubuntu 13.10 in UEFI mode alongside Windows 8 and when I add GRUB_CMDLINE_LINUX_DEFAULT="intel_pstate=enable" followed by grub-update, the option won't get enabled after reboot. acpi-cpufreq is still enabled.

---

### Post by Doug S on 2013-10-23
> **pnarciso said:**
> I'm running ubuntu 13.10 in UEFI mode alongside Windows 8 and when I add GRUB_CMDLINE_LINUX_DEFAULT="intel_pstate=enable" followed by grub-update, the option won't get enabled after reboot. acpi-cpufreq is still enabled.Perhaps your processor (being relatively new) hasn't been added to the supported processors list yet. Or if it has in the upstream driver, maybe it hasn't propagated to the mainstream Ubuntu 13.10 yet.

---

### Post by pnarciso on 2013-10-23
If I install 4.12 mainline kernel I have intel pstate enabled, but I can't enable it  in default 4.11 throught grub cmd.

---

### Post by pqwoerituytrueiwoq on 2013-10-23
> **mörgæs said:**
> Moved to General Help, as 13.10 is now an official release.not sure if should be there, intel_pstate is not enabled stock in the ubuntu kernel

---

### Post by Linuxisfast on 2013-10-23
pstate can be easily enabled via grub, just add intel_pstate=enable and it works, if you want to make it even more effective compile Intel Thermal Daemon from the git, it works well in conjunction with pstate to keep the CPU cool and efficient under high sustained load. Why pstate wasn't enabled in the kernel is beyond me. It works fine in every other distro.

---

### Post by Doug S on 2013-10-23
> **pqwoerituytrueiwoq said:**
> not sure if should be there, intel_pstate is not enabled stock in the ubuntu kernelI agree with pq...q. In my opinion this still a development subject, it just started with kernel 3.10, but continues with kernel 3.12

@pq...q: By the way, there were edits to intel_pstate.c in kernel 3.12RC6: "Fix max_perf_pct on resume". I had thought resume issues had long since been solved.

---

### Post by pqwoerituytrueiwoq on 2013-10-23
everything works for me like it should in 3.12
just a permissions issue in 3.11 (preserve across suspend)

---

