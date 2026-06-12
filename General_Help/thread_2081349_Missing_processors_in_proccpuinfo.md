---
title: "Missing processors in /proc/cpuinfo"
date: 2012-11-06
forum: General Help
---

### Post by sQua on 2012-11-06
Hi, I hope I'm posting in the right section,

I have just installed Ubuntu 12.10 desktop amd64 on a machine with an Intel Xeon E5-2665 CPU running @ 2.4GHz, which is 8 core (16 hyperthreads), but when I do a [COLOR=DarkRed]cat /proc/cpuinfo[/COLOR], I only get listed hyperthreads 0-7 (the first 8 of 16).  It's definately listing hyperthreads, as it lists each one as 1.2GHz with an overall clock of 2.4GHz.  If hyperthreading was off, it would list each one as 2.4GHz.

In the BIOS, it is set to enable hyperthreading, and, I have also booted Fedora 17, and doing a [COLOR=DarkRed]cat /proc/cpuinfo[/COLOR] it gives hyperthreads 0-15 (all 16).

Is there is a reason my other hyperthreads don't appear in [COLOR=DarkRed]/proc/cpuinfo[/COLOR]?  Are they missing and can't be used?

---

### Post by ibjsb4 on 2012-11-06
The Xeon E5-2665 does indeed have 16 threads (two threads per core), but that is not the same as hyperthreading.  Hyperthreading makes one physical core appear as two.  So you would see 8 or a total of 16 cores.

[http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

---

### Post by rnerwein on 2012-11-07
> **sQua said:**
> Hi, I hope I'm posting in the right section,

I have just installed Ubuntu 12.10 desktop amd64 on a machine with an Intel Xeon E5-2665 CPU running @ 2.4GHz, which is 8 core (16 hyperthreads), but when I do a [COLOR=DarkRed]cat /proc/cpuinfo[/COLOR], I only get listed hyperthreads 0-7 (the first 8 of 16).  It's definately listing hyperthreads, as it lists each one as 1.2GHz with an overall clock of 2.4GHz.  If hyperthreading was off, it would list each one as 2.4GHz.

In the BIOS, it is set to enable hyperthreading, and, I have also booted Fedora 17, and doing a [COLOR=DarkRed]cat /proc/cpuinfo[/COLOR] it gives hyperthreads 0-15 (all 16).

Is there is a reason my other hyperthreads don't appear in [COLOR=DarkRed]/proc/cpuinfo[/COLOR]?  Are they missing and can't be used?

hi
have a look at:    /sys/devices/system/cpu/cpu0/cpufreq
there you will find: via ls
affected_cpus     cpuinfo_transition_latency     scaling_governor
bios_limit             related_cpus                                      scaling_max_freq
cpb                            scaling_available_frequencies  scaling_min_freq
cpuinfo_cur_freq  scaling_available_governors     scaling_setspeed
cpuinfo_max_freq  scaling_cur_freq                          stats
cpuinfo_min_freq  scaling_driver

then: cat scaling_governor --> ondemand --> that means the cpu will speed up if the
system is under load.
in --> cpuinfo_cur_freq you will see the current speed. this value will go to cpuinfo_max_freq if the system is under load.

by

---

### Post by sQua on 2012-11-07
> **ibjsb4 said:**
> The Xeon E5-2665 does indeed have 16 threads (two threads per core), but that is not the same as hyperthreading. Hyperthreading makes one physical core appear as two. So you would see 8 or a total of 16 cores.

[http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

Yep.  But only 8 cores are appearing on [COLOR=DarkRed]/proc/cpuinfo[/COLOR].

I no longer have Fedora 17 installed, as I wrote over it with the Ubuntu installation, but when I did a [COLOR=DarkRed]cat /proc/cpuinfo[/COLOR] in that, it listed 16 cores (0..15), whereas under Ubuntu, it lists 8 cores (0..7).

Though I just realised I ended up installing Ubuntu Desktop 12.10 from a magazine cover disc, which is the 32 bit (i386/i686) version, rather than the 64 bit (x86_64/amd64) version I downloaded as I had no CD to burn it on.  I don't know if this makes a difference.  I didn't realise that it was 32 bit until now, doing a uname -a.

> **rnerwein said:**
> hi
have a look at: /sys/devices/system/cpu/cpu0/cpufreq
there you will find: via ls
affected_cpus cpuinfo_transition_latency scaling_governor
bios_limit related_cpus scaling_max_freq
cpb scaling_available_frequencies scaling_min_freq
cpuinfo_cur_freq scaling_available_governors scaling_setspeed
cpuinfo_max_freq scaling_cur_freq stats
cpuinfo_min_freq scaling_driver

then: cat scaling_governor --> ondemand --> that means the cpu will speed up if the
system is under load.
in --> cpuinfo_cur_freq you will see the current speed. this value will go to cpuinfo_max_freq if the system is under load.

by


Catting the files under [COLOR=DarkRed]/sys/devices/system/cpu/cpu0/cpufreq/[/COLOR] gives:

Ubuntu Desktop 12.10: [COLOR=DarkRed] Linux Precision-T7600 3.5.0-15-generic #23-Ubuntu SMP ... i686 i686 i686 GNU/Linux[/COLOR]:
```
affected_cpus                  0
bios_limit                     2401000
cpuinfo_cur_freq               1200000
cpuinfo_max_freq               2401000
cpuinfo_min_freq               1200000
cpuinfo_transition_latency     10000
related_cpus                   0 1 2 3 4 5 6 7
scaling_available_frequencies  2401000 2400000 2200000 2000000 1800000 1600000 1400000 1200000
scaling_available_governors    conservative ondemand userspace powersave performance
scaling_cur_freq               1200000
scaling_driver                 acpi-cpufreq
scaling_governor               ondemand
scaling_max_freq               2401000
scaling_min_freq               1200000
scaling_setspeed               <unsupported>

```Catting the files under A pre-beta Fedora 18 (18-Beta-TC7):  [COLOR=DarkRed]Linux localhost 3.6.5-2.fc18.x86_64 #1 SMP ... x86_64 x86_64 x86_64 GNU/Linux[/COLOR]:
```
affected_cpus                  0
bios_limit                     2401000
cpuinfo_cur_freq               1200000
cpuinfo_max_freq               2401000
cpuinfo_min_freq               1200000
cpuinfo_transition_latency     10000
related_cpus                   0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15
scaling_available_frequencies  2401000 2400000 2200000 2000000 1800000 1600000 1400000 1200000
scaling_available_governors    conservative userspace powersave ondemand performance
scaling_cur_freq               1200000
scaling_driver                 acpi-cpufreq
scaling_governor               ondemand
scaling_max_freq               2401000
scaling_min_freq               1200000
scaling_setspeed               <unsupported>

```So, from this, it seems under Ubuntu half my cores are not accessible.  Is this because it is the 32 bit version? - Would this change if I installed the 64 bit version (which I should anyway)?

---

### Post by mcduck on 2012-11-07
The frequency has nothing to do with Hyperthreading, or the amount of cores visible to the kernel. Ubuntu is showing the cores running at 1.2GHz because the CPU frequency is scaled based on load, and the CPU is not currently doing enough work to make it switch to a higher speed.

(a 2.4GHz CPU core with hyperthreading enabled will not appear as 2*1.2GHz CPU cores, it will appear as two 2.4GHz CPU cores.)

Anyway, your problem is simply that while Ubuntu's 32-bit kernel has both SMP and hyperthreading enabled, it's only compiled to support maximum of 8 CPUs/cores. Installing the 64-bit version will fix your problem.

(it's not a 32-bit OS limitation, though, so you *could* recompile the kernel manually and set it to allow more cores, but you'll get much better performance from running a 64-bit OS anyway.)

---

### Post by ibjsb4 on 2012-11-07
xxx

Edit: Did not know that mcduck.  Thought 32 bit was 32 core capable.

---

### Post by sQua on 2012-11-07
Which are more than 8 core capable?  Because there is the Ubuntu Desktop version, in 32 bit and 64 bit, and the Ubuntu Server, in 32 bit and 64 bit.

Would I need the Server version?  Or will the 64 bit version of Ubuntu Desktop do?

BTW, I found in [COLOR=DarkRed]dmesg[/COLOR] ( [COLOR=DarkRed]| grep -i cpu[/COLOR] ) that it detected the other 8 "processor"s under Ubuntu:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000]   Transmeta TransmetaCPU
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] ACPI: SSDT 063b0018 36296 (v02  INTEL    CpuPm 00004000 INTL 20091112)
[    0.000000] ACPI: NR_CPUS/possible_cpus limit of 8 reached.  Processor 8/0x1 ignored.
[    0.000000] ACPI: NR_CPUS/possible_cpus limit of 8 reached.  Processor 9/0x3 ignored.
[    0.000000] ACPI: NR_CPUS/possible_cpus limit of 8 reached.  Processor 10/0x5 ignored.
[    0.000000] ACPI: NR_CPUS/possible_cpus limit of 8 reached.  Processor 11/0x7 ignored.
[    0.000000] ACPI: NR_CPUS/possible_cpus limit of 8 reached.  Processor 12/0x9 ignored.
[    0.000000] ACPI: NR_CPUS/possible_cpus limit of 8 reached.  Processor 13/0xb ignored.
[    0.000000] ACPI: NR_CPUS/possible_cpus limit of 8 reached.  Processor 14/0xd ignored.
[    0.000000] ACPI: NR_CPUS/possible_cpus limit of 8 reached.  Processor 15/0xf ignored.
[    0.000000] 32 Processors exceeds NR_CPUS limit of 8
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7b79000 s34176 r0 d23168 u57344
[    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
[    0.000000] Initializing CPU#0
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000256] Initializing cgroup subsys cpuacct
[    0.000296] CPU: Physical Processor ID: 0
[    0.000297] CPU: Processor Core ID: 0
[    0.000302] mce: CPU supports 20 MCE banks
[    0.000330] CPU0: Thermal monitoring enabled (TM1)
[    0.065674] CPU0: Intel(R) Xeon(R) CPU E5-2665 0 @ 2.40GHz stepping 07
[    0.172325] PEBS disabled due to CPU errata.
[    0.172479] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.172551] CPU 1 irqstacks, hard=f7574000 soft=f7576000
[    0.184397] Initializing CPU#1
[    0.186654] CPU 2 irqstacks, hard=f75ae000 soft=f75b0000
[    0.197363] Initializing CPU#2
[    0.199869] CPU 3 irqstacks, hard=f75ba000 soft=f75bc000
[    0.210570] Initializing CPU#3
[    0.213074] CPU 4 irqstacks, hard=f75d2000 soft=f75d4000
[    0.223776] Initializing CPU#4
[    0.226274] CPU 5 irqstacks, hard=f75e6000 soft=f75f0000
[    0.236968] Initializing CPU#5
[    0.239480] CPU 6 irqstacks, hard=f75fa000 soft=f75fc000
[    0.250169] Initializing CPU#6
[    0.252683] CPU 7 irqstacks, hard=f762e000 soft=f7630000
[    0.263365] Initializing CPU#7
[    0.265848] Brought up 8 CPUs
[    0.464447] ACPI: Requesting acpi_cpufreq
[    1.047699] cpuidle: using governor ladder
[    1.048079] cpuidle: using governor menu
[    1.691792] microcode: CPU0 sig=0x206d7, pf=0x1, revision=0x70b
[    1.719760] microcode: CPU1 sig=0x206d7, pf=0x1, revision=0x70b
[    1.720655] microcode: CPU2 sig=0x206d7, pf=0x1, revision=0x70b
[    1.721529] microcode: CPU3 sig=0x206d7, pf=0x1, revision=0x70b
[    1.722419] microcode: CPU4 sig=0x206d7, pf=0x1, revision=0x70b
[    1.723349] microcode: CPU5 sig=0x206d7, pf=0x1, revision=0x70b
[    1.724294] microcode: CPU6 sig=0x206d7, pf=0x1, revision=0x70b
[    1.725416] microcode: CPU7 sig=0x206d7, pf=0x1, revision=0x70b
[    1.737708] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.744023] radeon 0000:05:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffdf4c00
```...but [COLOR=DarkRed]NR_CPUS[/COLOR] is set to just 8 in 32 bit Ubuntu Desktop 12.10.

I'm just curious, is the only way to change this via a kernel recompile?

If anyone is running 64 bit Ubuntu Desktop, can you check that [COLOR=DarkRed]NR_CPUS[/COLOR] is higher?

Thanks everyone. I need to go 64 bit anyway, so it'll be some days before I buy a CD/DVD to burn it on.

BTW. [COLOR=DarkRed]NR_CPUS[/COLOR] seems to be set to 128 in F18-Beta-TC7, runtime limited to 32 via [COLOR=DarkRed]nr_cpu_ids[/COLOR], though I was using the 64 bit version there (running from DVD):
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] ACPI: SSDT 00000000063b0018 36296 (v02  INTEL    CpuPm 00004000 INTL 20091112)
[    0.000000] smpboot: Allowing 32 CPUs, 16 hotplug CPUs
[    0.000000] setup_percpu: NR_CPUS:128 nr_cpumask_bits:128 nr_cpu_ids:32 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88084f200000 s84288 r8192 d22208 u131072
[    0.000000] pcpu-alloc: s84288 r8192 d22208 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 
[    0.000000] pcpu-alloc: [0] 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=32, Nodes=1
[    0.000000]     RCU restricting CPUs from NR_CPUS=128 to nr_cpu_ids=32.
[    0.012146] Initializing cgroup subsys cpuacct
[    0.012192] CPU: Physical Processor ID: 0
[    0.012193] CPU: Processor Core ID: 0
[    0.012198] mce: CPU supports 20 MCE banks
[    0.012227] CPU0: Thermal monitoring enabled (TM1)
[    0.045461] smpboot: CPU0: Intel(R) Xeon(R) CPU E5-2665 0 @ 2.40GHz stepping 07
[    0.146359] perf_event_intel: PEBS disabled due to CPU errata, please upgrade microcode
[    0.147111] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.346750] Brought up 16 CPUs
[    6.432912] ACPI: Requesting acpi_cpufreq
[    6.564780] cpuidle: using governor ladder
[    6.565386] cpuidle: using governor menu
[   10.685353] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.700622] radeon 0000:05:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff88083bbe5c00
[   29.700836] microcode: CPU0 sig=0x206d7, pf=0x1, revision=0x70b
[   32.382086] microcode: CPU1 sig=0x206d7, pf=0x1, revision=0x70b
[   32.382876] microcode: CPU2 sig=0x206d7, pf=0x1, revision=0x70b
[   32.383564] microcode: CPU3 sig=0x206d7, pf=0x1, revision=0x70b
[   32.384233] microcode: CPU4 sig=0x206d7, pf=0x1, revision=0x70b
[   32.384981] microcode: CPU5 sig=0x206d7, pf=0x1, revision=0x70b
[   32.385863] microcode: CPU6 sig=0x206d7, pf=0x1, revision=0x70b
[   32.386636] microcode: CPU7 sig=0x206d7, pf=0x1, revision=0x70b
[   32.387159] microcode: CPU8 sig=0x206d7, pf=0x1, revision=0x70b
[   32.387821] microcode: CPU9 sig=0x206d7, pf=0x1, revision=0x70b
[   32.388404] microcode: CPU10 sig=0x206d7, pf=0x1, revision=0x70b
[   32.388729] microcode: CPU11 sig=0x206d7, pf=0x1, revision=0x70b
[   32.389313] microcode: CPU12 sig=0x206d7, pf=0x1, revision=0x70b
[   32.389605] microcode: CPU13 sig=0x206d7, pf=0x1, revision=0x70b
[   32.389891] microcode: CPU14 sig=0x206d7, pf=0x1, revision=0x70b
[   32.390274] microcode: CPU15 sig=0x206d7, pf=0x1, revision=0x70b
```

---

### Post by mcduck on 2012-11-08
Both desktop and server 64-bit kernels are compiled to support 256 cores.

And like I said, yes, you can recompile the 32-bit kernel and enable support for up to 256 cores on it (set "BIGSMP=y" in kernel options), but installing the 64-bit version would be a much better idea, especially since you said the 32-bit setup is a fresh install and therefore you wouldn't loose anything if you make the switch now...

---

