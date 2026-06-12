---
title: "CPU frequency at max with powersave governor"
date: 2015-08-23
forum: General Help
---

### Post by black veils on 2015-08-23
had this laptop for about 8 months. i have tried many different setups due to hardware problems, i finally was getting by ok with a specific kernel, but still left with a bad crashing problem, which happens infrequently, but is inevitable. which is why i recently upgraded my 14.04.1 with the hardware enablement stack, bringing me to the equivalent of 15.04 i think, for hardware support.

my battery is draining within 4 hours, when it used to last 7, which is what prompted me to check the frequency. i just learned the newer kernel manages cpu frequency differently, using pstate. i found pstate can be disabled but i'm not sure how much would get affected by that, and i figure i should try and stay with the new way if possible. i know about things like TLP, but i only want to make it have functioning 'powersave' mode. i've lost patience with all the searching about this stuff, so here i am. thanks for reading.

```
uname -r
3.19.0-25-generic

```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
1900000

```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq
800000

```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
performance powersave

```

```
cat /sys/devices/system/cpu/intel_pstate/no_turbo
1

```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
powersave

```

it used to be at 800, now its as if in performannce mode:
```
inxi -C
CPU:       Dual core Intel Core i3-4030U CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) 
           Clock Speeds: 1: 1900.00 MHz 2: 1900.00 MHz 3: 1899.925 MHz 4: 1900.00 MHz
```

```
inxi -Fxz
System:    Host: Aspire-E5-571 Kernel: 3.19.0-25-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Xfce 4.11.6 (Gtk 2.24.23) Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Acer model: EA50_HB version: V1.04 Bios: Insyde version: V1.04 date: 05/06/2014
CPU:       Dual core Intel Core i3-4030U CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 7582.08 
           Clock Speeds: 1: 1900.00 MHz 2: 1900.00 MHz 3: 1900.00 MHz 4: 1872.761 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.17.1 driver: intel Resolution: 1366x768@60.1hz 
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 10.5.2 Direct Rendering: Yes
Audio:     Card-1: Intel Lynx Point-LP HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Card-2: Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-25-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k bus-ID: 02:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: 3000 bus-ID: 01:00.1
           IF: eth0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (4.1% used) 1: id: /dev/sda model: ST500LT012 size: 500.1GB 
Partition: ID: / size: 87G used: 19G (24%) fs: ext4 ID: swap-1 size: 4.19GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 47.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 221 Uptime: 1:17 Memory: 1315.8/3843.6MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17
```

---

### Post by Doug S on 2015-08-23
Please note that "powersave" mode with the acpi-cpufreq frequency scaling driver is different than "powersave" mode with the intel_pstate driver. Really intel_pstate "powersave" is roughly equivalent to acpi-cpufreq "ondemand".

Your high CPU frequency might just be due to the load. For desktops, an "idle" system is not actually idle at all, and maybe there is enough stuff going on to cause the driver to raise up the frequency. For servers, an "idle" system is typically has much much less to do that a desktop, and the CPU frequency will tend to be lower. Anyway, the reported CPU frequency does not tell the whole story, one also has to consider how much time is spent in the C0 state (active) and various other C states (various levels of idle, where higher C states use less power). The turbostat utility is the best tool (my opinion) to really know what is going on.

You can force the lowest CPU frequency with the intel_pstate driver (the equivalent of "powersave" mode with the acpi-cpufreq driver) by adjusting  /sys/devices/system/cpu/intel_pstate/max_perf_pct.
You could also just use the acpi-cpufreq driver and use "powersave" mode to force the lowest CPU frequency.

---

### Post by black veils on 2015-08-23
yes i know its different, the new way 'powersave' is more like the old way 'on-demand'. it didnt used to be on max, and now it is - which for me is a waste.

```
./turbostat -d sleep 10

CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:45:1 (6:69:1)
CPUID(6): APERF, DTS, PTM, EPB
RAPL: 17476 sec. Joule Counter Range, at 15 Watts
cpu0: MSR_NHM_PLATFORM_INFO: 0x8083bf3011300
8 * 100 = 800 MHz max efficiency frequency
19 * 100 = 1900 MHz base frequency
cpu0: MSR_IA32_POWER_CTL: 0x0004005f (C1E auto-promotion: ENabled)
cpu0: MSR_TURBO_RATIO_LIMIT: 0x13131313
19 * 100 = 1900 MHz max turbo 4 active cores
19 * 100 = 1900 MHz max turbo 3 active cores
19 * 100 = 1900 MHz max turbo 2 active cores
19 * 100 = 1900 MHz max turbo 1 active cores
cpu0: MSR_NHM_SNB_PKG_CST_CFG_CTL: 0x1e008405 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=5: pc7s)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000000 (performance)
cpu0: MSR_CORE_PERF_LIMIT_REASONS, 0x04000000 (Active: ) (Logged: PkgPwrL1, )
cpu0: MSR_GFX_PERF_LIMIT_REASONS, 0x14000000 (Active: ) (Logged: PkgPwrL1, )
cpu0: MSR_RING_PERF_LIMIT_REASONS, 0x0c000000 (Active: ) (Logged: PkgPwrL1, PkgPwrL2, )
cpu0: MSR_RAPL_POWER_UNIT: 0x000a0e03 (0.125000 Watts, 0.000061 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x00000078 (15 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x804280c800dd80c8 (locked)
cpu0: PKG Limit #1: ENabled (25.000000 Watts, 28.000000 sec, clamp ENabled)
cpu0: PKG Limit #2: ENabled (25.000000 Watts, 0.002441* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00640000 (100 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x88360800 (46 C)
cpu0: MSR_IA32_THERM_STATUS: 0x88360800 (46 C +/- 1)
cpu2: MSR_IA32_THERM_STATUS: 0x88360800 (46 C +/- 1)
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 Pkg%pc8 Pkg%pc9 Pk%pc10 PkgWatt CorWatt GFXWatt
       -       -      85    4.56    1873    1896       0   49.94    4.99    1.77   38.74      44      46   22.30    0.00    0.00    0.00    0.00    0.00    0.00    5.50    0.51    1.87
       0       0     159    8.49    1867    1896       0   32.65    8.77    2.64   47.45      44      46   22.30    0.00    0.00    0.00    0.00    0.00    0.00    5.50    0.51    1.87
       0       1      31    1.65    1877    1896       0   39.49
       1       2     116    6.16    1879    1896       0   61.71    1.21    0.90   30.02      44
       1       3      37    1.95    1877    1896       0   65.92
10.000955 sec
```

---

### Post by Doug S on 2015-08-23
> **black veils said:**
> seems i cant install that utility, as its part of another package, which is meant for kernel 3.13.0, is there another way i can monitor to provide some more info here?
Yes, that is very annoying, as turbsotat really isn't dependent on kernel version (within reason). Anyway, I PM'd you a spot where a recently compiled turbostat is located on my web site.

Note that it might also help to use powertop to help identify the actual power consumption culprits.

Edit 1: I had not seen your edit when I replied. Yes, the CPU frequency does seem a little high relative to the load. Also the CPUs are spending less time in C7 and more time in C1 than one might expect. One suggestion might be some higher frequency type events, preventing the system from deciding to put the CPU into C7.

Edit2: Also this:```
MSR_IA32_ENERGY_PERF_BIAS: 0x00000000 (performance)
```is supposed to be this:```
MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
```although tests I have [done]("https://bugzilla.kernel.org/attachment.cgi?id=177961") never revealed any difference due to this setting. (and I don't think it was ever figured out how it got set to performance, I don't recall for sure.)

---

### Post by black veils on 2015-08-23
how would i find out what these events might be? it must be directly related to the hardware enablement upgrade i did, as i havent changed anything else.

---

### Post by Doug S on 2015-08-23
Your issue sounds similar to [this one]("https://bugzilla.kernel.org/show_bug.cgi?id=92111"). It might be worth trying [kernel 4.2RC7]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-rc7-unstable/")

---

### Post by black veils on 2015-08-23
so what would you recommend doing, as an alternate to trying different kernels? i'm guessing try reverting to the old method: intel-pstate=disable. - if i did that, is there anything else i would need to do?

---

### Post by Doug S on 2015-08-23
Yes, try using the acpi-cpufreq frequency scaling driver. No you shouldn't need to do anything else other than disable the intel_pstate driver in the grub command line. Please report back here.

Are you unwilling to try kernel 4.2RC7? That kernel has a change in the intel_pstate driver that will allow better trace data, if we get to it. If you are uncomfortable trying other kernels and such, that is fine.

powertop might also provide additional insight.

---

### Post by black veils on 2015-08-24
i tried with --time=10 option for powertop, but it didnt seem to work, just stays constantly running. so i simply ran 'powertop'.

```
Summary: 2936.7 wakeups/second,  363.6 GPU ops/seconds, 0.0 VFS ops/sec and 25.7% CPU use

                Usage       Events/s    Category       Description
             31.6 ms/s     1728.8       Process        compton -b
             45.2 ms/s     373.5        Process        plank
             54.2 ms/s     430.5        Process        /usr/lib/firefox/firefox
              4.7 ms/s     338.1        Interrupt      [48] i915
             70.6 ms/s      59.0        Process        /usr/bin/X -bs -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
            531.2 µs/s      60.0        Process        [rcu_sched]
            307.6 µs/s      60.0        kWork          intel_unpin_work_fn
            243.3 µs/s      60.0        kWork          intel_mmio_flip_work_func
             26.2 ms/s      41.3        Process        skype %U
            251.1 µs/s      31.5        kWork          gen6_pm_rps_work
              1.1 ms/s      14.7        Process        [rcuos/0]
            324.4 µs/s      13.8        Process        [rcuos/2]
              1.2 ms/s      11.8        Process        /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libcpugraph.so 2 18
              3.1 ms/s      10.8        Process        /home/vicky/.dropbox-dist/dropbox-lnx.x86_64-3.8.6/dropbox
              1.1 ms/s      10.8        Timer          tick_sched_timer
             16.3 µs/s       9.8        kWork          i915_gem_file_idle_work_handler
              0.8 ms/s       7.9        Process        /usr/bin/xfce4-terminal
            116.3 µs/s       8.8        kWork          ieee80211_iface_work
            654.2 µs/s       4.9        Process        psensor
              4.6 ms/s       2.0        Process        /opt/SpiderOak/lib/SpiderOak --spider
             27.7 µs/s       2.9        Interrupt      [4] block(softirq)
              2.1 ms/s       2.0        Process        /opt/SpiderOak/lib/SpiderOak
            137.4 µs/s       2.0        Process        /usr/lib/accountsservice/accounts-daemon
            119.4 µs/s       2.0        Process        rsyslogd
              0.9 ms/s       1.0        Interrupt      [7] sched(softirq)
            570.9 µs/s       1.0        Interrupt      [6] tasklet(softirq)
             94.4 µs/s       1.0        Process        NetworkManager
             55.7 µs/s       1.0        kWork          bdi_writeback_workfn
             54.0 µs/s       1.0        Process        upstart-dbus-bridge --daemon --session --user --bus-name session
             30.5 µs/s       1.0        Process        zeitgeist-datahub
             19.3 µs/s       1.0        kWork          flush_to_ldisc
             10.9 µs/s       1.0        Process        [watchdog/0]
              9.3 µs/s       1.0        Process        /opt/SpiderOak/lib/inotify_dir_watcher 3130 /home/vicky/.config/SpiderOak/config.txt /home/vicky/.config/SpiderOak/
              3.9 µs/s       1.0        Process        [watchdog/3]

```

yes i know how to try different kernels, and i have done that a lot for this laptop, with bad results, i really just cant deal with it anymore. i was reluctant to try the one i have now, but obviously by changing nothing, i will still have the eventual crash problem. i have had surprisingly good results with this kernel (crashing aside, as its too early to tell), but there is at least one bad looking thing in the logs. anyway thats why i dont want to kernel-hop, it would be never-ending as there are so many versions, and this laptop is meant to be generic but has a precarious existence with Linux Distro's.

thanks for the help.


**Edit:  I have disabled intel_pstate.**
```

# inxi -C  every second
count=1; while [ "$count" -lt "16" ]; do inxi -C | grep "Clock Speeds"; let "count=count+1"; sleep 1; done
           Clock Speeds: 1: 900.00 MHz 2: 800.00 MHz 3: 1100.00 MHz 4: 800.00 MHz
           Clock Speeds: 1: 800.00 MHz 2: 1000.00 MHz 3: 1000.00 MHz 4: 800.00 MHz
           Clock Speeds: 1: 900.00 MHz 2: 900.00 MHz 3: 900.00 MHz 4: 1900.00 MHz
           Clock Speeds: 1: 800.00 MHz 2: 900.00 MHz 3: 900.00 MHz 4: 1700.00 MHz
           Clock Speeds: 1: 1000.00 MHz 2: 1000.00 MHz 3: 779.00 MHz 4: 1900.00 MHz
           Clock Speeds: 1: 1700.00 MHz 2: 900.00 MHz 3: 900.00 MHz 4: 800.00 MHz
           Clock Speeds: 1: 1600.00 MHz 2: 900.00 MHz 3: 900.00 MHz 4: 800.00 MHz
           Clock Speeds: 1: 800.00 MHz 2: 900.00 MHz 3: 1200.00 MHz 4: 800.00 MHz
           Clock Speeds: 1: 800.00 MHz 2: 900.00 MHz 3: 800.00 MHz 4: 779.00 MHz
           Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz 3: 900.00 MHz 4: 1000.00 MHz
           Clock Speeds: 1: 900.00 MHz 2: 900.00 MHz 3: 1600.00 MHz 4: 800.00 MHz
           Clock Speeds: 1: 1200.00 MHz 2: 800.00 MHz 3: 900.00 MHz 4: 1000.00 MHz
           Clock Speeds: 1: 800.00 MHz 2: 1000.00 MHz 3: 1100.00 MHz 4: 800.00 MHz
           Clock Speeds: 1: 900.00 MHz 2: 800.00 MHz 3: 900.00 MHz 4: 800.00 MHz
           Clock Speeds: 1: 1000.00 MHz 2: 800.00 MHz 3: 900.00 MHz 4: 900.00 MHz
```

```
sudo ./turbostat -d sleep 10
turbostat version 4.7 27-May, 2015 - Len Brown <lenb@kernel.org>
CPUID(0): GenuineIntel 13 CPUID levels; family:model:stepping 0x6:45:1 (6:69:1)
CPUID(6): APERF, DTS, PTM, EPB
RAPL: 17476 sec. Joule Counter Range, at 15 Watts
cpu0: MSR_NHM_PLATFORM_INFO: 0x8083bf3011300
8 * 100 = 800 MHz max efficiency frequency
19 * 100 = 1900 MHz base frequency
cpu0: MSR_IA32_POWER_CTL: 0x0004005d (C1E auto-promotion: DISabled)
cpu0: MSR_TURBO_RATIO_LIMIT: 0x13131313
19 * 100 = 1900 MHz max turbo 4 active cores
19 * 100 = 1900 MHz max turbo 3 active cores
19 * 100 = 1900 MHz max turbo 2 active cores
19 * 100 = 1900 MHz max turbo 1 active cores
cpu0: MSR_NHM_SNB_PKG_CST_CFG_CTL: 0x1e008405 (UNdemote-C3, UNdemote-C1, demote-C3, demote-C1, locked: pkg-cstate-limit=5: pc7s)
cpu0: MSR_IA32_ENERGY_PERF_BIAS: 0x00000006 (balanced)
cpu0: MSR_CORE_PERF_LIMIT_REASONS, 0x00000000 (Active: ) (Logged: )
cpu0: MSR_GFX_PERF_LIMIT_REASONS, 0x10000000 (Active: ) (Logged: )
cpu0: MSR_RING_PERF_LIMIT_REASONS, 0x0c000000 (Active: ) (Logged: PkgPwrL1, PkgPwrL2, )
cpu0: MSR_RAPL_POWER_UNIT: 0x000a0e03 (0.125000 Watts, 0.000061 Joules, 0.000977 sec.)
cpu0: MSR_PKG_POWER_INFO: 0x00000078 (15 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x804280c800dd80c8 (locked)
cpu0: PKG Limit #1: ENabled (25.000000 Watts, 28.000000 sec, clamp ENabled)
cpu0: PKG Limit #2: ENabled (25.000000 Watts, 0.002441* sec, clamp DISabled)
cpu0: MSR_PP0_POLICY: 0
cpu0: MSR_PP0_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: Cores Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_PP1_POLICY: 0
cpu0: MSR_PP1_POWER_LIMIT: 0x00000000 (UNlocked)
cpu0: GFX Limit: DISabled (0.000000 Watts, 0.000977 sec, clamp DISabled)
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x00640000 (100 C)
cpu0: MSR_IA32_PACKAGE_THERM_STATUS: 0x88370800 (45 C)
cpu0: MSR_IA32_THERM_STATUS: 0x88380000 (44 C +/- 1)
cpu2: MSR_IA32_THERM_STATUS: 0x88380000 (44 C +/- 1)
    Core     CPU Avg_MHz   %Busy Bzy_MHz TSC_MHz     SMI  CPU%c1  CPU%c3  CPU%c6  CPU%c7 CoreTmp  PkgTmp Pkg%pc2 Pkg%pc3 Pkg%pc6 Pkg%pc7 Pkg%pc8 Pkg%pc9 Pk%pc10 PkgWatt CorWatt GFXWatt
       -       -      81    8.12     994    1896       0   54.25    4.20    1.08   32.36      44      45    4.83    0.00    0.00    0.00    0.00    0.00    0.00    6.60    0.47    2.04
       0       0      85    8.43    1002    1896       0   67.62    3.91    1.22   18.82      44      45    4.83    0.00    0.00    0.00    0.00    0.00    0.00    6.60    0.47    2.04
       0       1     107   10.97     973    1896       0   65.08
       1       2      85    8.53     993    1896       0   40.15    4.50    0.93   45.89      44
       1       3      47    4.54    1030    1896       0   44.14
10.002236 sec

```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
1901000
```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq
779000
```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance
```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
ondemand
```

---

### Post by Doug S on 2015-08-24
O.K., but your package power is actually a little bit higher (small sample time, and only one sample). How is your battery life?

---

### Post by black veils on 2015-08-24
what does that means exactly? I assume it's from the turbostat output.

I removed the battery yesterday, I will have to put it back in and see.

---

### Post by Doug S on 2015-08-24
> **black veils said:**
> what does that means exactly? I assume it's from the turbostat output.
I removed the battery yesterday, I will have to put it back in and see.I was just saying that your total processor package power increased by about 1.1watts, and so I don't know that you achieved your objective of gaining back battery life.

Yes, I extracted the information from your turbostat postings.

---

