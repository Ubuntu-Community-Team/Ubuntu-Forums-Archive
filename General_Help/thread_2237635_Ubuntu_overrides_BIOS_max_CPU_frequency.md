---
title: "Ubuntu overrides BIOS max CPU frequency?"
date: 2014-08-03
forum: General Help
---

### Post by 5mZKCMUmw1Le on 2014-08-03
Hi all,

I've attempted to overclock my CPU, a Pentium G3258. I've turned off all intel power saving (states) and turbo.
Setting a frequency like 3.3GHz or 4GHz results in the following outputs:

```
cat /proc/cpuinfo | grep "MHz":

cpu MHz        : 3200.146
cpu MHz        : 3200.146
```

```
sudo dmidecode -t processor | grep Speed
    Max Speed: 3800 MHz
    Current Speed: 3200 MHz

```

3.2GHz is the stock speed. The output of the commands do not change under full load.


My hypothesis is that Ubuntu overrides the BIOS with some sort of dynamic CPU frequency scaling, and incorrectly uses the stock speed as the max.

Which sort of CPU frequency scaling does Ubuntu use, and how confirm/discard my hypothesis?

Thanks!

---

### Post by tgalati4 on 2014-08-03
Install a cpu speed applet on your dock or panel and I bet you will see it switch between 3.2 and 3.8 GHz.  The fact that it recognizes the current speed and the maximum speed gives you an indication that kernel recognizes the stepping appropriate for your CPU.

There are a number of cpu-speed handling utilities available:

> tgalati4@Mint14-Extensa ~ $ apt-cache search cpufreq
mate-applets - Various applets for the MATE panel
mate-applets-common - Various applets for the MATE panel (common files)
collectd-core - statistics collection and monitoring daemon (core system)
cpufreqd - fully configurable daemon for dynamic frequency and voltage scaling
cpufrequtils - utilities to deal with the cpufreq Linux kernel feature
gnome-applets - Various applets for the GNOME panel - binary files
indicator-cpufreq - CPU frequency scaling indicator
libcpufreq-dev - development files to deal with the cpufreq Linux kernel feature
libcpufreq0 - shared library to deal with the cpufreq Linux kernel feature
xfce4-cpufreq-plugin - cpufreq information plugin for the Xfce4 panel
xfce4-goodies - enhancements for the Xfce4 Desktop Environment

---

### Post by 5mZKCMUmw1Le on 2014-08-03
Hello,

Thank you for your reply. 

I have indicator-cpufreq installed and it does not go above 3.2GHz even under full load. My CPU should be able to hit far above 3.8GHz, and right now it is set @ 4 GHz in BIOS.

Do you have any other suggestions?
Thanks!

---

### Post by DogMatix on 2014-08-03
Have you tried

```
sudo dmidecode
```

and checked current speed there?

EDIT: Sorry I see you have.

I had a similar issue. But it turned out that the overclocking was working. I tend to believe my BIOS with such matters now.

+ dmidecode does show my 'current' speed overclocked to what I expect so our issues must be different!

---

### Post by 3rdalbum on 2014-08-03
Your BIOS is the problem. You need yo turn off speed scaling in the BIOS and then the CPU will run at your new speed. Nothing to do with Ubuntu.

---

### Post by 5mZKCMUmw1Le on 2014-08-04
> **3rdalbum said:**
> Your BIOS is the problem. You need yo turn off speed scaling in the BIOS and then the CPU will run at your new speed. Nothing to do with Ubuntu.

Hello,
I can see that this may not have been clear from the first post, but:

- Intel Turbo Boost is disabled
- C1E is disabled
- C3 state support is disabled
- C6/7 state support is disabled
- CPU EIST Function (Intel Speed Step Technology) is disabled

I'm not sure if Speed Step and speed scaling is the same, but I'm unable to find such a setting in my BIOS.
Anyway - this should not matter as i am running the CPU under 100% load, and hence shouldn't it be using the highest frequency possible?

Regards,

---

### Post by 3rdalbum on 2014-08-04
No idea then, but you keep mentioning that you have set the BIOS to 4GHz. On my motherboard you don't set the CPU speed directly, you alter the bus speed and multiplier, and through some simple maths you work out what the CPU speed will be. I have a Core 2 which obviously works differently to the newer Core CPUs with no Northbridge.

But my point is: Are you sure you are over clocking correctly? Have you done this successfully before?

---

### Post by tgalati4 on 2014-08-04
Check the processor and motherboard compatibility.  Not all motherboard settings will work with a specific CPU.  There are voltage restrictions, front side bus speed restrictions, multiplier restrictions.  All it takes is hitting one limitation and speed step will not work.  For that you will have to do some research.  Post a portion of the dmesg during bootup that details the CPU detection.

```
dmesg | more
```

What version of Ubuntu?  What kernel version?

```
uname -a
```

---

### Post by Xvani on 2014-08-04
Hello,

I'm the OP, just switched nicks. I'm running a Gigabyte Z97N-Gaming 5 MB with my G3258 CPU. BIOS is updated to specifically support this CPU.
Thank you for your continued help!

> **3rdalbum said:**
> But my point is: Are you sure you are over clocking correctly? Have you done this successfully before?

I'm setting the multiplier and the BCLK (40*100MHz). The BIOS states that the CPU is running at 4GHz, so I'm pretty sure Ubuntu is doing something.
I've overclocked plenty back when it was just FSB and multipliers, but never on this specific setup. There are however, [plenty of guides]("http://www.overclock.net/t/1490835/the-gigabyte-z97x-overclocking-guide")

> **tgalati4 said:**
> Check the processor and motherboard compatibility.  Not all motherboard settings will work with a specific CPU.  There are voltage restrictions, front side bus speed restrictions, multiplier restrictions.  All it takes is hitting one limitation and speed step will not work.  For that you will have to do some research.  Post a portion of the dmesg during bootup that details the CPU detection.

```
dmesg | more
```



I'm barely touching any settings though, and they should all be supported by the CPU, which is largely unlocked. "Speed step" is disabled, although enabling it doesn't do anything.

```
$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-32-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 (Ubuntu 3.13.0-32.57-gener
ic 3.13.11.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=7f488ae0-5516-4dca-ac71-7b581cf7cf95 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
```


> **tgalati4 said:**
> 
What version of Ubuntu?  What kernel version?

```
uname -a
```

Ubuntu 14.04

```
$ uname -a
Linux ###### 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Hope this helps!

Thanks

---

### Post by Xvani on 2014-08-04
some more dmesg outputs:
```

$ dmesg |grep cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] KERNEL supported cpus:
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88022fa00000 s86336 r8192 d24256 u1048576
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=2.
[    0.082930] cpuidle: using governor ladder
[    0.082931] cpuidle: using governor menu
[    0.454559] ledtrig-cpu: registered to indicate activity on CPUs

```

```

$ dmesg |grep MHz
[    0.004000] tsc: Detected 3199.768 MHz processor
[    0.159690] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.390045] tsc: Refined TSC clocksource calibration: 3199.996 MHz

```

---

### Post by tgalati4 on 2014-08-04
An interesting link on *cpuidle*:  [http://www.fsl.cs.sunysb.edu/docs/cpuidle/cpuidle-from-userspace.pdf](http://www.fsl.cs.sunysb.edu/docs/cpuidle/cpuidle-from-userspace.pdf)

You will have to spend some time getting into the details.  

```
cat /proc/cpuinfo
```

Grab an older distro (12.04) USB stick and boot off of that and examine your CPU speeds.  It could be a 3.13 kernel regression (if it ever worked correctly) or a bug (CPU speeds don't work at all).

I have an older Core2Duo that switches between 2GHz and 2.66GHz very rapidly.  So fast, that I thought it wasn't working correctly because I could never see (or verify) the faster "turbo" speeds.  Install *cpuburn* and run a few instances to really push your machine, then you might see the faster speeds.

---

### Post by Xvani on 2014-08-10
Hi,

This problem was due to a BIOS bug. I solved it by resetting the BIOS to defaults, and changing the frequencies again. Thanks for all your help!

---

