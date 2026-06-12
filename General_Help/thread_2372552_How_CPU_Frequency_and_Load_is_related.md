---
title: "How CPU Frequency and Load is related"
date: 2017-09-26
forum: General Help
---

### Post by anspectrum on 2017-09-26
Hello,

This is not a particular issue rather a general understanding query and as such should be *nix agnostic.

I am using 16.04 on i7 processor (Quad Core) and was doing some reading about processes behavior when a process gets shifted from one CPU core to another. There is sometimes noticeable performance degradation while executing a program on multi-core (multi-threaded) architecture due to CPU cache population. So while doing the reading I did some simple tests on my machine and found an interesting observation and hence this post.

I've written a simple C program, compiled and run it. This program is supposed to stress test a CPU to the maximum. While I execute the program, I am also having an (almost) realtime observation at the CPUs that how there processing power is behaving, using commands

```
watch -n 1 'cpufreq-info | grep "current CPU"'
```  and ```
top
``` as well as GUI System Monitor

Now this stress program is a single threaded program and I can see in the output of top and System Monitor that single CPU is being loaded to 100%. However, cpufreq-info output shows that all 4 CPUs have got there frequencies jacked up. I've also tried using the command ```
taskset
``` to restrict the program to use only one CPU but cpufreq-info output still shows that all 4 CPUs are cranked up.

Can someone suggest why ```
cpufreq-info
``` shows all CPUs being used while ```
top
``` and GUI System Monitor show otherwise ??

---

### Post by efflandt on 2017-09-26
I am not familiar with cpufreq-info, so not sure what it displays. But there can be a difference between showing "thread" frequencies and "core" frequencies. For example the attached is an example showing glxgears, which as far as I know maxes out one thread if not using vsync. It is an old i7 870 2.93 GHz (3.6 GHz turbo), but good enough for me for now (a little slower than newer i5). The only other apps open were firefox on ubuntuforms.org and gedit in different desktops. Terminal windows are displaying:

glxgears  (left)|(right)  a script I wrote that greps MHz from /proc/cpuinfo every 5 seconds which just shows stock speeds, not turbo (tried to time screenshot just after it output)
htop  (left)|(right)  i7z

Note that htop shows thread 7 at 100%, but glxgears using 106% cpu (due to turbo).
Note that i7z shows "all" of the cores bumped up in frequency beyond stock 2.93 GHz.

I don't think it would be possible to max out one thread or core and monitor that without some other thread or core doing something (and there are other background processes). Even when only running glxgears and i7z I had trouble trying to capture the core beyond its 24x multiplier (for more turbo of less than 3 cores in use) while running glxgears. I know at least one game from Feral (DiRT Rally) that assigns specific tasks to specific cores based on how many cores and threads you have to give more of the cpu to tasks that need it and groups less busy tasks on other cores to balance out the load.

So maybe when you need it the whole CPU gets cranked up, but less used cores would have more idle states than at lower speed.

i7z also mentions that cpuinfo may not be correct if using cpufreq.

---

### Post by anspectrum on 2017-09-27
Try this, I am uploading C code (Just one line O:) ). Compile and run it. And while doing so you can use the same cpuinfo command as ```
watch -n 1 'cat /proc/cpuinfo | grep MHz'
``` and GUI System Monitor in parallel. You would see similar output as in the screenshots that I've attached. Now here is the puzzle that why all the CPU cores / threads have cranked up their frequencies while only one is being shown as loaded as per System Monitor ?

_C Code_
```
void main(int argc, char **argv) { while(1); }
```

[U]Commands Output
[https://pasteboard.co/GMgpvS2.png](https://pasteboard.co/GMgpvS2.png)
[/U]
[U]System Monitor
[https://pasteboard.co/GMgsg5k.png](https://pasteboard.co/GMgsg5k.png)
[/U]

---

### Post by anspectrum on 2017-10-04
Bump :(

---

### Post by Doug S on 2017-10-04
Please note that the use of "grep MHz /proc/cpuinfo" will no longer work as of kernel 4.13. That line of the /proc/cpuinfo file will only show tsc and not the actual or requested (depending on the CPU frequency scaling driver used) CPU frequency. A look at the CPU frequencies will require this command:

```
cat /sys/devices/system/cpu/cpufreq/policy*/scaling_cur_freq
```

While future plans differ, current Intel processors use one CPU frequency PLL (Phase Locked Loop) for all cores. Meaning that there is only one active CPU frequency possible, regardless of load. That CPU frequency is typically determined by the CPU with the maximum load. While the unloaded CPUs will use a higher than needed CPU frequency while active, they will spend a lot of their time in a deep idle state, using little to no energy.

A very good tool to use for this stuff is turbostat (part of the linux-tools-common, I think (I compile it myself)). Example (where CPU 7 is loaded, and the others are more or less idle):

```
doug@s15:~$ [COLOR="#FF0000"]sudo turbostat --hide SMI,C1,C1E,C3,C6,GFX%rc6,GFXMHz sleep 10[/COLOR]
turbostat version 17.06.23 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
CPUID(1): SSE3 MONITOR - EIST TM2 TSC MSR ACPI-TM TM
CPUID(6): APERF, TURBO, DTS, PTM, No-HWP, No-HWPnotify, No-HWPwindow, No-HWPepp, No-HWPpkg, EPB
cpu0: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST No-MWAIT PREFETCH TURBO)
CPUID(7): No-SGX
cpu0: MSR_MISC_PWR_MGMT: 0x00400000 (ENable-EIST_Coordination DISable-EPB DISable-OOB)
RAPL: 690 sec. Joule Counter Range, at 95 Watts
cpu0: MSR_PLATFORM_INFO: 0x100070012200
16 * 100.0 = 1600.0 MHz max efficiency frequency
34 * 100.0 = 3400.0 MHz base frequency
cpu0: MSR_IA32_POWER_CTL: 0x0004005d (C1E auto-promotion: DISabled)
cpu0: MSR_TURBO_RATIO_LIMIT: 0x23242526
35 * 100.0 = 3500.0 MHz max turbo 4 active cores
36 * 100.0 = 3600.0 MHz max turbo 3 active cores
37 * 100.0 = 3700.0 MHz max turbo 2 active cores
38 * 100.0 = 3800.0 MHz max turbo 1 active cores
cpu0: MSR_PKG_CST_CONFIG_CONTROL: 0x1e008403 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=3: pc6r)
cpu0: POLL: CPUIDLE CORE POLL IDLE
cpu0: C1: MWAIT 0x00
cpu0: C1E: MWAIT 0x01
cpu0: C3: MWAIT 0x10
cpu0: C6: MWAIT 0x20
cpu0: cpufreq driver: intel_pstate
cpu0: cpufreq governor: powersave
cpufreq intel_pstate no_turbo: 0
cpu0: MSR_MISC_FEATURE_CONTROL: 0x00000000 (L2-Prefetch L2-Prefetch-pair L1-Prefetch L1-IP-Prefetch)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a1003 (0.125000 Watts, 0.000015 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x01e002f8 (95 W TDP, RAPL 60 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x800087f8001487f8 (locked)
cpu0: PKG Limit #1: ENabled (255.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: ENabled (255.000000 Watts, 0.000977* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00621200 (98 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x88310000 (49 C)
cpu0: MSR_IA32_PACKAGE_THERM_INTERRUPT: 0x00000003 (98 C, 98 C)
cpu0: MSR_PKGC3_IRTL: 0x00008850 (valid, 81920 ns)
cpu0: MSR_PKGC6_IRTL: 0x00008868 (valid, 106496 ns)
cpu0: MSR_PKGC7_IRTL: 0x0000886d (valid, 111616 ns)
10.001075 sec
Core    CPU     Avg_MHz Busy%   Bzy_MHz TSC_MHz IRQ     C1%     C1E%    C3%     C6%     CPU%c1  CPU%c3  CPU%c6  CPU%c7  CoreTmp PkgTmp  Pkg%pc2 Pkg%pc3 Pkg%pc6 PkgWatt CorWatt GFXWatt
-       -       478     12.53   3799    3411    2777    0.01    0.00    0.00    87.46   12.57   0.00    74.90   0.00    49      49      0.00    0.00    0.00    23.53   18.85   0.24
0       0       1       0.02    3644    3411    41      0.00    0.00    0.00    99.98   0.19    0.00    [COLOR="#FF0000"]99.79[/COLOR]   0.00    41      49      0.00    0.00    0.00    23.53   18.85   0.24
0       4       6       0.17    3700    3411    15      0.00    0.00    0.00    99.83   0.04
1       1       1       0.02    3685    3411    68      0.00    0.00    0.00    99.98   0.03    0.00    [COLOR="#FF0000"]99.95[/COLOR]   0.00    42
1       5       0       0.01    3626    3411    22      0.00    0.00    0.00    99.99   0.04
2       2       1       0.02    3680    3411    60      0.10    0.00    0.00    99.89   0.13    0.00    [COLOR="#FF0000"]99.85[/COLOR]   0.00    43
2       6       0       0.01    3663    3411    46      0.01    0.01    0.00    99.98   0.14
3       3       0       0.00    3786    3411    20      0.00    0.00    0.00    100.00  100.00  0.00    [COLOR="#FF0000"]0.00[/COLOR]    0.00    49
3       7       3811    [COLOR="#FF0000"]99.97[/COLOR]   [COLOR="#FF0000"]3800[/COLOR]    3411    2505    0.00    0.00    0.00    0.00    0.03
```
Notes:
[LIST]
[*]I hide some columns because: They are relatively new; To fit my server screen width.
[*]My older i7 processor does not go into idle level C7, it can only go to C6.
[*]3800 MHz Busy Mega Hertz is actually incorrect, it is 3811 MHz. While it didn't used to, turbostat now uses an approximation of 100 MHz per pstate for this calculation.
[/LIST]

---

