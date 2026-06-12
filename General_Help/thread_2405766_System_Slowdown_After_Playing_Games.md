---
title: "System Slowdown After Playing Games"
date: 2018-11-10
forum: General Help
---

### Post by hyottositara on 2018-11-10
I have a Thinkpad X1 Yoga 3rd Gen. Everything works fine, except when I start a game or something else equally demanding on the processor, and after a minute or two, the system suddenly slows down significantly. Even if I quit the game, the system is unusable even on the desktop with nothing running. It takes 15-20 seconds for it to react to things like clicking on the "Show Application" button. The problem only goes away after a restart. It doesn't seem to be thermal throttling because the fans aren't running and even after waiting it doesn't go away.

I don't see anything in System Monitor that seems to be the culprit, but my CPU is under moderate load.

---

### Post by hyottositara on 2018-11-14
So, I think I found the problem.
The CPU is getting locked at a very low speed:

cat /proc/cpuinfo | grep MHz
cpu MHz        : 134.408
cpu MHz        : 123.880
cpu MHz        : 210.849
cpu MHz        : 140.726
cpu MHz        : 174.872
cpu MHz        : 124.567
cpu MHz        : 152.535
cpu MHz        : 191.205

I have no idea why this is happening or how to fix it.

---

### Post by Doug S on 2018-11-14
We need to know your processor, what CPU frequency scaling driver and governor you are using, and what kernel version. Examples:

```
doug@s15:~/temp$ [COLOR="#FF0000"]grep "model name" /proc/cpuinfo | head -1[/COLOR]
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave
doug@s15:~/temp$ [COLOR="#FF0000"]uname -a[/COLOR]
Linux s15 4.20.0-rc1-teo5 #520 SMP PREEMPT Sat Nov 10 23:49:44 PST 2018 x86_64 x86_64 x86_64 GNU/Linux

```It looks as though Clock Modulation is being enabled (probably as a result of a too hot situation), but it is being set awfully aggressive. The intel_pstate driver used to be fundamentally incompatible with Clock Modulation, but that was fixed some time ago.

to check for Clock Modulation do this (you need the msr-tools package):
```
sudo modprobe msr
sudo rdmsr 0x19a -a
```Post the results, and I'll decode it (I don't recall how to at the moment).
To prevent getting so hot as to trigger Clock Modulation, which is done by the BIOS in some computers, in the first place I would suggest thermald, but toss out the default config file and try [this one]("https://askubuntu.com/questions/897217/cpu-overheating-on-ubuntu-16-04-msi-ge40/897856#897856"). You could also try tlp (I think is the name), but i have never used it.

---

### Post by hyottositara on 2018-11-14
First, thank you for taking the time to look at this. I really appreciate it!

Here's the output:
```
[COLOR=#FF0000]grep "model name" /proc/cpuinfo | head -1[/COLOR]
model name    : Intel(R) Core(TM) i7-8650U CPU @ 1.90GHz

[COLOR=#FF0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate[COLOR=#FF0000]

cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave

[COLOR=#FF0000]uname -a[/COLOR]
Linux Tako 4.18.0-10-generic #11-Ubuntu SMP Thu Oct 11 15:13:55 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

sudo modprobe msr
(no output)
sudo rdmsr 0x19a -a
0
0
0
0
0
0
0
0
```

I invoked the last two in the throttled state just to be sure. I'll try that example configuration file.
EDIT: The configuration file seems to cause the fan to run sooner, but doesn't stop the problem from occurring.

---

### Post by Doug S on 2018-11-14
Well, it isn't Clock Modulation, unless the "proc_hot" external bit is set. Your 8th generation processor is so new that maybe there is something about it the kernel doesn't know.

I am moving from stuff I know very well to speculation or long shots now:

Myself, I would try to disable HWP (hardware pstates) just for a test. To do so edit your /etc/default/grub file (save a copy first) and change whatever is on the GRUB_CMDLINE_LINUX_DEFAULT line by adding "intel_pstate=no_hwp". Example:

Change this:

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=300"
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=300 intel_pstate=no_hwp"
```

remember to update after:

```
sudo update-grub
```then re-boot and test.

Next, I would try to disable the intel_pstate CPU frequency scaling driver altogether, thus the acpi-cpufreq driver will be used. As above except:

```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 consoleblank=300 intel_pstate=disable"
```

Please note that the stuff already on the line is just an example from my computer, your existing line will probably be different, or even blank.

The only other suggestion is to use turbostat (part of the linux-tools-common package) to see if it tells us something in its big spew of stuff when it starts. Example:

```
doug@s15:~$ [COLOR="#FF0000"]sudo turbostat[/COLOR]
[sudo] password for doug:
turbostat version 18.07.27 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:2a:7 (6:42:7)
CPUID(1): SSE3 MONITOR - EIST TM2 TSC MSR ACPI-TM HT TM
CPUID(6): APERF, TURBO, DTS, PTM, No-HWP, No-HWPnotify, No-HWPwindow, No-HWPepp, No-HWPpkg, EPB
cpu1: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST MWAIT PREFETCH TURBO)
CPUID(7): No-SGX

... snip - big spew of stuff continues. Any hint here? ...]

```
EDIT: Actually running turbostat might be good idea in general. Suggest something like this (spew of stuff disabled for this), where I load up the CPUs after 30 seconds:

```
doug@s15:~$ sudo turbostat --quiet --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXMHz,GFXWatt --interval 15
Busy%   Bzy_MHz PkgTmp  GFXMHz  PkgWatt GFXWatt
0.01    1600    25      850     3.67    0.12
0.01    1600    26      850     3.67    0.12
49.90   3514    48      850     36.79   0.12
100.00  3500    54      850     58.61   0.12
100.00  3500    58      850     59.30   0.12
100.00  3500    63      850     59.94   0.12
100.00  3500    65      850     60.97   0.12
100.00  3500    68      850     61.48   0.12
100.00  3500    68      850     61.81   0.12

```

---

### Post by hyottositara on 2018-11-15
You can see where it craters here:

```
sudo turbostat --quiet --Summary --show Busy%,Bzy_MHz,PkgTmp,PkgWatt,GFXMHz,GFXWatt --interval 3[FONT=courier new]
Busy%  Bzy_MHz PkgTmp GFXMHz  PkgWatt  GFXWatt
 5.96     787    54     300     1.97     0.01
 8.60    1255    54     583     2.69     0.04
 7.47     955    54     300     2.32     0.05
 6.26    1382    59    1150     2.86     0.21
 6.83    1489    54     300     3.26     0.42
25.93    2630    65     300    10.69     0.47
14.02    2156    58     300     6.39     0.36
16.64    2045    74     300     6.40     0.43
13.49    1941    58     300     5.39     0.25
32.19    3114    84     300    17.54     0.53
28.83    3225    85     300    17.01     0.48
21.12    3299    86     867    15.38     0.28
14.75    3140    85     300    11.75     0.03
13.31    3085    85     300    10.41     0.10
16.17    3240    75     300    12.22     0.00
12.68    2640    81     300     8.39     0.01
32.05    2888    82    1150    16.89     4.74
24.84    1855    85    1150    17.85    10.56
18.74    2883    85    1150    18.16     8.63
17.03    2815    85    1150    16.80     8.14
18.10    2685    87    1150    15.30     7.11
17.66    2625    86    1150    15.25     7.35
17.01    2989    86    1150    17.31     8.01
17.55    2880    85    1150    18.16     9.23
18.25    1783    86    1150    16.71    11.04
18.24    1816    85    1150    17.13    11.46
25.98    1099    73    1150    10.85     6.15
34.64     400    70    1150     3.07     0.34
44.60     282    67     300     2.78     0.14
40.26     209    64     300     2.44     0.00
24.93     187    63     300     2.24     0.00
34.33     195    62     317     2.45     0.02
22.21     173    60     300     2.25     0.04
21.19     138    59     300     2.13     0.01[/FONT]
```[FONT=courier new]

[FONT=arial]I'll try the kernel commandline change next and report back.[/FONT]
[/FONT]

---

### Post by hyottositara on 2018-11-15
So, I got the same behavior with those two options: "no_hwp" and "disable." I did verify in dmesg that they were applied. Not sure where to go from here. Thanks for your time, in any case?

Oh, and here's the full turbostat spew:
```
turbostat version 18.07.27 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 22 CPUID levels; family:model:stepping 0x6:8e:a (6:142:10)
CPUID(1): SSE3 MONITOR SMX EIST TM2 TSC MSR ACPI-TM HT TM
CPUID(6): APERF, TURBO, DTS, PTM, HWP, HWPnotify, HWPwindow, HWPepp, No-HWPpkg, EPB
cpu0: MSR_IA32_MISC_ENABLE: 0x00850089 (TCC EIST MWAIT PREFETCH TURBO)
CPUID(7): SGX
cpu0: MSR_IA32_FEATURE_CONTROL: 0x00040005 (Locked SGX)
CPUID(0x15): eax_crystal: 2 ebx_tsc: 176 ecx_crystal_hz: 0
TSC: 2112 MHz (24000000 Hz * 176 / 2 / 1000000)
CPUID(0x16): base_mhz: 2100 max_mhz: 4200 bus_mhz: 100
cpu0: MSR_MISC_PWR_MGMT: 0x00401cc0 (ENable-EIST_Coordination DISable-EPB DISable-OOB)
RAPL: 17476 sec. Joule Counter Range, at 15 Watts
cpu0: MSR_PLATFORM_INFO: 0x804043df1011500
4 * 100.0 = 400.0 MHz max efficiency frequency
21 * 100.0 = 2100.0 MHz base frequency
cpu0: MSR_IA32_POWER_CTL: 0x0024005d (C1E auto-promotion: DISabled)
cpu0: MSR_TURBO_RATIO_LIMIT: 0x27272a2a
39 * 100.0 = 3900.0 MHz max turbo 4 active cores
39 * 100.0 = 3900.0 MHz max turbo 3 active cores
42 * 100.0 = 4200.0 MHz max turbo 2 active cores
42 * 100.0 = 4200.0 MHz max turbo 1 active cores
cpu0: MSR_CONFIG_TDP_NOMINAL: 0x00000013 (base_ratio=19)
cpu0: MSR_CONFIG_TDP_LEVEL_1: 0x00080050 (PKG_MIN_PWR_LVL1=0 PKG_MAX_PWR_LVL1=0 LVL1_RATIO=8 PKG_TDP_LVL1=80)
cpu0: MSR_CONFIG_TDP_LEVEL_2: 0x001500c8 (PKG_MIN_PWR_LVL2=0 PKG_MAX_PWR_LVL2=0 LVL2_RATIO=21 PKG_TDP_LVL2=200)
cpu0: MSR_CONFIG_TDP_CONTROL: 0x00000000 ( lock=0)
cpu0: MSR_TURBO_ACTIVATION_RATIO: 0x00000012 (MAX_NON_TURBO_RATIO=18 lock=0)
cpu0: MSR_PKG_CST_CONFIG_CONTROL: 0x1e008008 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked, pkg-cstate-limit=8 (unlimited))
cpu0: POLL: CPUIDLE CORE POLL IDLE
cpu0: C1: MWAIT 0x00
cpu0: C1E: MWAIT 0x01
cpu0: C3: MWAIT 0x10
cpu0: C6: MWAIT 0x20
cpu0: C7s: MWAIT 0x33
cpu0: C8: MWAIT 0x40
cpu0: C9: MWAIT 0x50
cpu0: C10: MWAIT 0x60
cpu0: cpufreq driver: intel_pstate
cpu0: cpufreq governor: powersave
cpufreq intel_pstate no_turbo: 0
cpu0: MSR_MISC_FEATURE_CONTROL: 0x00000000 (L2-Prefetch L2-Prefetch-pair L1-Prefetch L1-IP-Prefetch)
cpu0: MSR_PM_ENABLE: 0x00000000 (No-HWP)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_RAPL_POWER_UNIT: 0x000a0e03 (0.125000 Watts, 0.000061 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x00000078 (15 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x43816000dd8001 (UNlocked)
cpu0: PKG Limit #1: ENabled (0.125000 Watts, 28.000000 sec, clamp ENabled)
cpu0: PKG Limit #2: ENabled (44.000000 Watts, 0.002441* sec, clamp ENabled)
cpu0: MSR_DRAM_POWER_LIMIT: 0x5400de00000000 (UNlocked)
cpu0: DRAM Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x0f640000 (100 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x88300c02 (52 C)
cpu0: MSR_IA32_PACKAGE_THERM_INTERRUPT: 0x00000003 (100 C, 100 C)
cpu0: MSR_PKGC3_IRTL: 0x0000884e (valid, 79872 ns)
cpu0: MSR_PKGC6_IRTL: 0x00008876 (valid, 120832 ns)
cpu0: MSR_PKGC7_IRTL: 0x00008894 (valid, 151552 ns)
cpu0: MSR_PKGC8_IRTL: 0x000088fa (valid, 256000 ns)
cpu0: MSR_PKGC9_IRTL: 0x0000894c (valid, 339968 ns)
cpu0: MSR_PKGC10_IRTL: 0x00008bf2 (valid, 1034240 ns)
Core    CPU    Avg_MHz    Busy%    Bzy_MHz    TSC_MHz    IRQ    SMI    POLL    C1    C1E    C3    C6    C7s    C8    C9    C10    POLL%    C1%    C1E%    C3%    C6%    C7s%    C8%    C9%    C10%    CPU%c1    CPU%c3    CPU%c6    CPU%c7    CoreTmp    PkgTmp    GFX%rc6    GFXMHz    Totl%C0    Any%C0    GFX%C0    CPUGFX%    Pkg%pc2    Pkg%pc3    Pkg%pc6    Pkg%pc7    Pkg%pc8    Pkg%pc9    Pk%pc10    CPU%LPI    SYS%LPI    PkgWatt    CorWatt    GFXWatt    RAMWatt    PKG_% RAM_%
-    -    6    2.99    199    2107    1637    0    1    97    37    26    114    1    594    9    1030    0.00    0.02    0.13    0.01    0.17    0.01    3.82    0.29    92.38    1.27    0.01    0.27    95.87    52    52    94.43    300    13.41    10.61    5.19    1.78    46.09    37.92    0.00    0.00    0.00    0.00    0.00    0.00    0.00    1.79    0.11    0.02    0.34    98.92 0.00


```

---

### Post by Doug S on 2018-11-15
Your processor seems to get awfully hot for not really very much load. It also hits TDP (Thermal Design Power) with not much load. I wonder if exceeding TDP causes issues (I've never exceeded it, and have no experience. I'll have to read [the book]("https://software.intel.com/en-us/download/intel-64-and-ia-32-architectures-sdm-combined-volumes-1-2a-2b-2c-2d-3a-3b-3c-3d-and-4") about it, but don't have time at the moment).

EDIT: These lines, from your turbostat spew, do not make sense to me:

```
cpu0: MSR_PKG_POWER_LIMIT: 0x43816000dd8001 (UNlocked)
cpu0: PKG Limit #1: ENabled (0.125000 Watts, 28.000000 sec, clamp ENabled)
cpu0: PKG Limit #2: ENabled (44.000000 Watts, 0.002441* sec, clamp ENabled)
```The package power limit 1?????

If this was my computer, and as a carefully controlled experiment, I would set the "Enable Power Limit #1" and "Package Clamping Limitation #1" bits of the MSR_PKG_POWER_LIMIT to zero.
For reference these are those 3 lines on my main test computer:

```
cpu0: MSR_PKG_POWER_LIMIT: 0x800087f8001487f8 (locked)
cpu0: PKG Limit #1: ENabled (255.000000 Watts, 1.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: ENabled (255.000000 Watts, 0.000977* sec, clamp DISabled)
```In my case the MSR is locked (I can not write to it), but in your case it isn't locked.

I wonder if it is a BIOS setting in your computer?

---

### Post by hyottositara on 2018-11-16
Hmm, yes, that spew is AFTER the slowdown. Before the slowdown, this is what it shows there:

 ```
cpu0: MSR_PKG_POWER_INFO: 0x00000078 (15 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x42016000dc8160 (UNlocked)
cpu0: PKG Limit #1: ENabled (44.000000 Watts, 28.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (44.000000 Watts, 0.002441* sec, clamp DISabled)
```

When you say "carefully controlled experiment," are you speaking in terms of being very cautious not to damage the computer by causing overheating in this case?
Nothing in the BIOS jumped out at me as related to this, but I can look again. EDIT: All I found that looked vaguely related were "Intel(R) Speedstep Technology [enabled/disabled]" and "CPU Power Management [enabled/disabled]," both currently enabled.

As far as the MSRs, I found wrmsr, but I don't know how to use it to write to a MSR.

---

### Post by Doug S on 2018-11-16
> **hyottositara said:**
> Hmm, yes, that spew is AFTER the slowdown. Before the slowdown, this is what it shows there:

 ```
cpu0: MSR_PKG_POWER_INFO: 0x00000078 (15 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x42016000dc8160 (UNlocked)
cpu0: PKG Limit #1: ENabled (44.000000 Watts, 28.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (44.000000 Watts, 0.002441* sec, clamp DISabled)
```O.K. the before slowdown makes sense. So now the question becomes what is making the change?

> **hyottositara said:**
> When you say "carefully controlled experiment," are you speaking in terms of being very cautious not to damage the computer by causing overheating in this case? Yes.


> **hyottositara said:**
> Nothing in the BIOS jumped out at me as related to this, but I can look again. EDIT: All I found that looked vaguely related were "Intel(R) Speedstep Technology [enabled/disabled]" and "CPU Power Management [enabled/disabled]," both currently enabled. Intel speedstep should be enabled. I'm not sure what the other one means, but perhaps try to disable it, just as a test.

> **hyottositara said:**
> As far as the MSRs, I found wrmsr, but I don't know how to use it to write to a MSR.I'll try to figure out what to do for a test, however it will only be on the weekend.

By the way, somewhere yesterday I read that a BIOS version (was it 1.26? (I don't recall for sure)) for your computer doesn't enable the fan soon enough and aggressively enough. Do you have the latest BIOS?

EDIT: as another bit of information, and after the slowdown, let's look at what Pstates are being asked for and what Pstates are given. Do:

```
$ sudo rdmsr --bitfield 15:8 -d -a 0x199
$ sudo rdmsr --bitfield 15:8 -d -a 0x198
```(remember to load the module (which turbostat does) first, "sudo modprobe msr", or you'll get nothing)

---

### Post by hyottositara on 2018-11-16
I double-checked the BIOS. I have the latest version, which for this laptop is 1.25.
The CPU Power Management BIOS setting didn't solve the issue.

Here are results after, with CPU Power Management at the default enabled setting. Note that before, the first was the same, but the second was all 20s:
```
sudo rdmsr --bitfield 15:8 -d -a 0x199
42
42
42
42
42
42
42
42
sudo rdmsr --bitfield 15:8 -d -a 0x198
4
4
4
4
4
4
4
4
```

---

### Post by Doug S on 2018-11-17
O.K., so the maximum turbo pstate is being asked for, but a pathetic pstate is being given. This appears to be due to the MSRs we have been looking at.
The plan, if your are willing.

Step 1, confirm that I have figured out the correct MSR, i.e. 610h (it isn't necessarily the same address on all processors). Do (the example is my processor):
```
sudo rdmsr 0x610
800087f8001487f8

``` and compare to the relevant line from the turbostat output:
```

cpu0: MSR_PKG_POWER_LIMIT: 0x800087f8001487f8 (locked)

```
Step 2, to be done after the slowdown situation (but don't play any games anymore), where your MSR reads as "0x43816000dd8001". Do:
```
sudo wrmsr 0x610 0x42016000dc0160
```check it with a subsequent rdmsr, and then check it with turbostat, you should get:
```
cpu0: MSR_PKG_POWER_LIMIT: 0x42016000dc[COLOR="#FF0000"]0[/COLOR]160 (UNlocked)
cpu0: PKG Limit #1: [COLOR="#FF0000"]DISabled[/COLOR] (44.000000 Watts, 28.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (44.000000 Watts, 0.002441* sec, clamp DISabled)
```
Step 3, will be to LOCK the register, but lets wait on that until the results from the above are known.

---

### Post by hyottositara on 2018-11-17
Step 1:
```
sudo rdmsr 0x610
42016000dc8160

sudo turbostat
...
cpu0: MSR_PKG_POWER_LIMIT: 0x42016000dc8160 (UNlocked)
...
```
The same.

Step 2:

```
sudo wrmsr 0x610 0x42016000dc0160
sudo rdmsr 0x610 42016000dc8160
sudo turbostat
...
cpu0: MSR_PKG_POWER_LIMIT: 0x42016000dc[COLOR=#ff0000]8[/COLOR]160 (UNlocked)
cpu0: PKG Limit #1: [COLOR=#ff0000]ENabled[/COLOR] (44.000000 Watts, 28.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (44.000000 Watts, 0.002441* sec, clamp DISabled)

```

So it changed, although the "disable" bit wasn't accepted, I guess? By the way, I'm able to write this message and use my computer relatively painlessly. Of course I didn't try running a game or anything like that after modifying the MSRs, but I can do things like write this response to you and restart the PC with normal performance.

---

### Post by andre802 on 2018-11-18
You have to reduce the number of "Startup Applications"


To do this:
Open up the Dash and type in "startup"
Remove few applications

---

### Post by Doug S on 2018-11-18
O.K., lets try to "lock" the register (after this step, you will need to re-boot to be able to revert the register). So step 2 again, but change the command to this:

```
sudo wrmsr 0x610 0x8042016000dc0160
```

---

### Post by hyottositara on 2018-11-18
Looks like that did, indeed, lock the register. I know there are some MSR tracing tools in the kernel, would it be possible to use those to track down what's changing it and causing the slowdown?:

```
cpu0: MSR_PKG_POWER_LIMIT: 0x8042016000dc8160 (locked)
cpu0: PKG Limit #1: ENabled (44.000000 Watts, 28.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (44.000000 Watts, 0.002441* sec, clamp DISabled)
```

Should I test with the MSR locked and see what happens?

---

### Post by mercyroy on 2018-11-19
i think you have to reduce your memory space and refresh frequently.

---

### Post by Doug S on 2018-11-19
> **hyottositara said:**
> Looks like that did, indeed, lock the register. I know there are some MSR tracing tools in the kernel, would it be possible to use those to track down what's changing it and causing the slowdown?:

```
cpu0: MSR_PKG_POWER_LIMIT: 0x8042016000dc8160 (locked)
cpu0: PKG Limit #1: ENabled (44.000000 Watts, 28.000000 sec, clamp DISabled)
cpu0: PKG Limit #2: DISabled (44.000000 Watts, 0.002441* sec, clamp DISabled)
```

Should I test with the MSR locked and see what happens? Yes, sure. There is still the thermal last line of defense if there is a problem. Myself, I would do a controlled experiment, ramping up CPU use and watch processor package power and temperature.

that being said, while the lock is working, it isn't locking to the desired contents, where package limit 1 is disabled. I'll re-check my decoding of the MSR.

I am not familiar with the MSR tracing tools in the kernel. I am familiar with, and use, trace under a few situations.

Note: I do not understand the other replies on this thread.

EDIT: As far as I can determine, my decoding of the MSR is correct. I do not know why we can not disable the package power limit #1, or in other words clear bit 15 of the register via writing  0x8042016000dc[COLOR="#FF0000"]0[/COLOR]160

---

### Post by hyottositara on 2018-11-22
Hmm, OK. Well, this does seem to fix the problem after a fashion, in that the system doesn't seem to slow down if I invoke  "sudo wrmsr 0x610 0x8042016000dc0160"

I think the root of the issue is whatever is setting this power limit, perhaps I'll try to open a Launchpad bug about it.

I don't understand enough about the power limit MSR to understand why you're trying to completely disable it, it seems like this is something that should always be enabled as a safety feature?

Thanks again for all your help!

---

### Post by Doug S on 2018-11-22
> **hyottositara said:**
> I don't understand enough about the power limit MSR to understand why you're trying to completely disable it, it seems like this is something that should always be enabled as a safety feature?You still have the thermal limit as a safety feature. For my processor this stuff is disabled.

Anyway, consider that what we did was just a test to prove that we had identified the correct culprit. Yes, it would be good to identify what is actually setting the ridiculous values in that MSR. My best guess is BIOS.

Let us know if you find out anything more. I am very interested in this.

EDIT: Some stuff I found:
[https://www.reddit.com/r/thinkpad/comments/90y3er/x1c6_bios_125_throttling/]("https://www.reddit.com/r/thinkpad/comments/90y3er/x1c6_bios_125_throttling/")
[https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/Thinkpad-X1-Carbon-6th-Gen-Bios-1-25-Performance/td-p/4148955]("https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/Thinkpad-X1-Carbon-6th-Gen-Bios-1-25-Performance/td-p/4148955")
[https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/TDP-Throttling-on-8250u-and-8550u/td-p/4029610]("https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/TDP-Throttling-on-8250u-and-8550u/td-p/4029610")

---

### Post by angisky on 2018-11-22
> **Doug S said:**
> We need to know your processor, what CPU frequency scaling driver and governor you are using, and what kernel version. Examples:

```
doug@s15:~/temp$ [COLOR=#FF0000]grep "model name" /proc/cpuinfo | head -1[/COLOR]
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
doug@s15:~/temp$ [COLOR=#FF0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
doug@s15:~/temp$ [COLOR=#FF0000]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave
doug@s15:~/temp$ [COLOR=#FF0000]uname -a[/COLOR]
Linux s15 4.20.0-rc1-teo5 #520 SMP PREEMPT Sat Nov 10 23:49:44 PST 2018 x86_64 x86_64 x86_64 GNU/Linux

```It looks as though Clock Modulation is being enabled (probably as a result of a too hot situation), but it is being set awfully aggressive. The intel_pstate driver used to be fundamentally incompatible with Clock Modulation, but that was fixed some time ago.

to check for Clock Modulation do this (you need the msr-tools package):
```
sudo modprobe msr
sudo rdmsr 0x19a -a
```Post the results, and I'll decode it (I don't recall how to at the moment).
To prevent getting so hot as to trigger Clock Modulation, which is done by the BIOS in some computers, in the first place I would suggest thermald, but toss out the default config file and try [this one]("https://askubuntu.com/questions/897217/cpu-overheating-on-ubuntu-16-04-msi-ge40/897856#897856"). You could also try tlp (I think is the name), but i have never used it.

Even though this link is from the arch wiki it'll work on ubuntu. All you have to do as a prerequisite is install linux tools using 


[LIST]
[*]sudo apt install linux-tools-common
[*]If it asks you to install another linux-tools related package when you try to run cpupower just install the one it tells you to. I had to install "linux-tools-4.15.0-39-generic" for compatibility. It also suggested a server package but installing that one gave me access to the command.
[*]Then just go to [https://wiki.archlinux.org/index.php/CPU_frequency_scaling](https://wiki.archlinux.org/index.php/CPU_frequency_scaling)
[*]That page tells you how to set your frequency scaling. You're on powersave right now so you're pegged at the lowest clock.
[/LIST]

---

### Post by Doug S on 2018-11-23
> **angisky said:**
> Even though this link is from the arch wiki it'll work on ubuntu. All you have to do as a prerequisite is install linux tools using 


[LIST]
[*]sudo apt install linux-tools-common
[*]If it asks you to install another linux-tools related package when you try to run cpupower just install the one it tells you to. I had to install "linux-tools-4.15.0-39-generic" for compatibility. It also suggested a server package but installing that one gave me access to the command.
[*]Then just go to [https://wiki.archlinux.org/index.php/CPU_frequency_scaling](https://wiki.archlinux.org/index.php/CPU_frequency_scaling)
[*]That page tells you how to set your frequency scaling. You're on powersave right now so you're pegged at the lowest clock.
[/LIST]The OP's CPU frequencies are much much lower than the normal minimum for the processor. When using the powersave governor with the intel_pstate driver the CPU frequencies are not pinned at the lowest pstate, however with the acpi-cpufreq driver the powersave governor does pin the pstate to its lowest value. It is just a personal preference, but I never ever use cpupower, however lots of users do and like it.

---

### Post by angisky on 2018-11-23
> **Doug S said:**
> The OP's CPU frequencies are much much lower than the normal minimum for the processor. When using the powersave governor with the intel_pstate driver the CPU frequencies are not pinned at the lowest pstate, however with the acpi-cpufreq driver the powersave governor does pin the pstate to its lowest value. It is just a personal preference, but I never ever use cpupower, however lots of users do and like it.

Look at the quote though. It's reporting that it's on powersave. I'm sure that is keeping the clocks low. If it was on performance you wouldn't see that.

---

### Post by Doug S on 2018-11-23
> **angisky said:**
> Look at the quote though. It's reporting that it's on powersave. I'm sure that is keeping the clocks low. If it was on performance you wouldn't see that.No, No. No, that is not true. For the intel_pstate CPU frequency driver, the powersave governor is roughly the equivalent of the ondemand governor for the acpi-cpufreq driver. Example, where awhile after starting turbostat, I add load to 1 CPU:
```
doug@s15:~$ grep . /sys/devices/system/cpu/cpufreq/policy*/scaling_driver
/sys/devices/system/cpu/cpufreq/policy0/scaling_driver:intel_pstate
...
/sys/devices/system/cpu/cpufreq/policy7/scaling_driver:intel_pstate
doug@s15:~$ grep . /sys/devices/system/cpu/cpufreq/policy*/scaling_governor
/sys/devices/system/cpu/cpufreq/policy0/scaling_governor:powersave
...
/sys/devices/system/cpu/cpufreq/policy7/scaling_governor:powersave
doug@s15:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt --interval 15
Busy%   Bzy_MHz PkgTmp  PkgWatt
0.03    1600    26      3.71
0.03    1600    27      3.71
0.03    1600    31      3.71
7.05    3791    41      14.43
12.53   [COLOR="#FF0000"]3799[/COLOR]    43      23.01
12.51   [COLOR="#FF0000"]3799[/COLOR]    45      23.10
^C

```EDIT: By the way, for the performance case, where only pstate 38 is ever asked for (my processor), if the load is low enough the processor itself will back off the CPU frequency:

```
doug@s15:~$ grep . /sys/devices/system/cpu/cpufreq/policy*/scaling_governor
/sys/devices/system/cpu/cpufreq/policy0/scaling_governor:performance
/sys/devices/system/cpu/cpufreq/policy1/scaling_governor:performance
/sys/devices/system/cpu/cpufreq/policy2/scaling_governor:performance
/sys/devices/system/cpu/cpufreq/policy3/scaling_governor:performance
/sys/devices/system/cpu/cpufreq/policy4/scaling_governor:performance
/sys/devices/system/cpu/cpufreq/policy5/scaling_governor:performance
/sys/devices/system/cpu/cpufreq/policy6/scaling_governor:performance
/sys/devices/system/cpu/cpufreq/policy7/scaling_governor:performance
doug@s15:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,PkgTmp,PkgWatt --interval 15
Busy%   Bzy_MHz PkgTmp  PkgWatt
0.01    1959    29      3.74
0.01    1919    28      3.73
0.01    1893    29      3.73
0.01    1823    28      3.72
0.01    1872    28      3.72
0.01    1883    28      3.72
^C
```

---

### Post by angisky on 2018-11-24
Oh so even after choosing a state the cpu still has control of it's own. Well unless it's a physical issue I don't know how the OS could be forcing that in anyway.

---

