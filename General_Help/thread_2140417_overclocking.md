---
title: "overclocking"
date: 2013-04-29
forum: General Help
---

### Post by Isaacmarritt on 2013-04-29
I have always woundering if there is a program for overclocking cpu or gpu on ubuntu or if it would work with my hardware. does anyone know anything about this subject.computer specs in my signature

---

### Post by Doug S on 2013-04-29
If your computer has variable clock rates, and if it is enabled in the BIOS, then linux should use it. Two examples are below, one from a computer that has it and one from a computer that doesn't:```
doug@doug-64:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor: No such file or directory
``````
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
```Now, on my computer that has variable clock rates, the rated freqcuency is 3.4 GHz. and if it is not busy, the clock is slowed:```
doug@s15:~/temp$ grep MHz /proc/cpuinfo
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
```But if I load down a cpu, then it will speed up:```
doug@s15:~/temp$ grep MHz /proc/cpuinfo
cpu MHz         : 3401.000     [COLOR=#ff0000]<<<<< The "1" on the end indicates that CPU is running overclocked, actually well above 3.4 GHz[/COLOR]
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
```

---

### Post by Isaacmarritt on 2013-04-30
unfurtonatly macbook do not have bios on it i was hopping there was  a linux program for over clocking    

isaac@isaacs-MacBookPro:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
ondemand
isaac@isaacs-MacBookPro:~$ /temp$ grep MHz /proc/cpuinfo
bash: /temp$: No such file or directory
isaac@isaacs-MacBookPro:~$ grep MHz /proc/cpuinfo
cpu MHz		: 800.000
cpu MHz		: 800.000

isaac@isaacs-MacBookPro:~$ grep MHz /proc/cpuinfo
cpu MHz		: 800.000
cpu MHz		: 800.000

---

### Post by kurja on 2013-04-30
isn't cpu clock controlled by efi? I doubt there would be linux programs to manipulate it from a ui but what do I know.

---

### Post by Doug S on 2013-04-30
So, you have it. You just need to load a CPU 100% to see the max clock rate.

---

### Post by Isaacmarritt on 2013-04-30
what do you mean load it as in run a run a  lot of programs to max out the cpu

---

### Post by Doug S on 2013-04-30
> **kurja said:**
> isn't cpu clock controlled by efi? I doubt there would be linux programs to manipulate it from a ui but what do I know.there are programs. I do not recall the name(s), as I do everything via primative commands from the terminal.

---

### Post by ZombieApocalypse on 2013-04-30
It's normal for your CPU to vary its clock speed according to load. This keeps the temperature down, saves energy and reduces fan noise.  3401 MHz is not overclocked. I wouldn't recommend overclocking in a laptop as your build won't have the ability to deal with the additional heat generated. 

Also for overclocking a CPU it is recommended that you only increase the CPU multiplier, which is locked on many processors. Increasing the base clock is risky because it also increases the clock on your memory.

---

### Post by Isaacmarritt on 2013-04-30
grep MHz /proc/cpuinfo
cpu MHz		: 800.000
cpu MHz		: 2200.000

---

### Post by Doug S on 2013-04-30
> **Isaacmarritt said:**
> what do you mean load it as in run a run a  lot of programs to max out the cpuYes, However, I just use one program that just uses the CPU at maximum. The other thing you can do is just force the cpu to max frequency. Example (run as "sudo"):```
doug@s15:~/sguide-1304/doug_check$ cat ~/temp/set_cpu_performance
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governorfor file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "performance" > $file; done
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```However, you should set is back to "ondemand" mode afterwards, or your computer might get hot, as it will always be running at max clock rate. There is also a list of available clock frequencies somewhere, but I didn't find it yet. 

If you are interested, and for intel CPU's, which you have, there is another way to know the real clock frequency, even when in turbo (overclocked mode). Let me know and I'll do another posting (after I try to remember the details).

---

### Post by Doug S on 2013-04-30
> **ZombieApocalypse said:**
> 3401 MHz is not overclocked.I disagree. When "1" is reported as the last digit, it means it is in turbo mode, and does not report the actual frequency. All we know is that is is above the rated frequency. So my same example again below but also using "turbostat" which reports the actual frequency of 3.81 Ghz:```
doug@s15:~/temp$ ./set_cpu_inquire
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
ondemand
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
[COLOR=#ff0000]cpu MHz         : 3401.000   <<< CPU 5 is in turbo mode[/COLOR]
cpu MHz         : 1600.000
cpu MHz         : 1600.000
doug@s15:~/temp$ sudo ./turbostat
 cr CPU    %c0  GHz  TSC    %c1    %c3    %c6    %c7  %pc2  %pc3  %pc6  %pc7
          12.52 3.81 3.41  14.06   0.02  73.40   0.00  0.00  0.00  0.00  0.00
   0   0   0.04 3.65 3.41   0.15   0.10  99.71   0.00  0.00  0.00  0.00  0.00
   0   4   0.04 3.66 3.41   0.15   0.10  99.71   0.00  0.00  0.00  0.00  0.00
   1   1   0.01 3.78 3.41  99.99   0.00   0.00   0.00  0.00  0.00  0.00  0.00
   1 [COLOR=#ff0000]  5  99.95 3.81 3.41   0.05   0.00   0.00   0.00  0.00  0.00  0.00  0.00   <<< CPU 5 is actually at 3.81 GHz.[/COLOR]
   2   2   0.03 3.65 3.41   4.01   0.00  95.97   0.00  0.00  0.00  0.00  0.00
   2   6   0.03 3.60 3.41   4.01   0.00  95.97   0.00  0.00  0.00  0.00  0.00
   3   3   0.03 3.70 3.41   2.06   0.00  97.91   0.00  0.00  0.00  0.00  0.00
   3   7   0.02 3.59 3.41   2.07   0.00  97.91   0.00  0.00  0.00  0.00  0.00
```

Edit: I found the list of available frequencies (which depends on the governore mode):```
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
```

---

### Post by Isaacmarritt on 2013-04-30
OK I got it to max usages is there a way to it to go past the  2200.00 celling  my cpu is programmed for

isaac@isaacs-MacBookPro:~$ grep MHz /proc/cpuinfo
cpu MHz		: 2200.000
cpu MHz		: 2200.000

---

### Post by Yellow Pasque on 2013-04-30
@Doug: Turbo boost is preprogrammed into the CPU and approved by the CPU vendor. It's not really OC'ing in the traditional sense. 

> **Isaacmarritt said:**
> OK I got it to max usages is there a way to it to go past the  2200.00 celling  my cpu is programmed for

If your BIOS doesn't support it, then no. 

Do you really think Apple wants its users getting more MHz without paying for them? Do you really think Apple wants to pay to replace hardware after users burn it out with OC'ing?
Note: ^those are rhetorical questions. What I'm getting at is that OC'ing is frowned upon in the walled garden..

---

### Post by Doug S on 2013-04-30
> **Temüjin said:**
> @Doug: Turbo boost is preprogrammed into the CPU and approved by the CPU vendor. It's not really OC'ing in the traditional sense.Thanks for the clarification. And yes, I do mix the two terminologies (turbo boost Verses overclocking). I would never ever overclock as you mean it.

---

