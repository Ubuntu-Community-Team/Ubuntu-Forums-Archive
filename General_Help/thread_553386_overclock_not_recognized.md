---
title: "overclock not recognized?"
date: 2007-09-17
forum: General Help
---

### Post by PurposeOfReason on 2007-09-17
A while ago I overclocked my CPU from 2.0GHZ to 2.7GHz. The BIOS shows this and has no trouble with it however if I bring up the system monitor in Ubuntu is still shows both cores at 2.00GHz. But then again, if I add $(freq_dyn} to my conky setup, it shows the correct speed. So is it not noticed by Ubuntu or is the system monitor displaying the wrong information?

---

### Post by southernman on 2007-09-17
If conky sees it, it must be a gnome thing. Can't be certain on this, but seems you think the same thing.

Have you run any test (before and after) to see if there is indeed a speed increase?

---

### Post by david_2001 on 2007-09-19
The gnome system monitor is reporting the cpuid, so what the cpu thinks it should be rather than its present state.  A "cat /proc/cpuinfo" should be more informative.  Here's what I get for my mildly overclocked Pentium D 820:

```
david@darkstar:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :               Intel(R) Pentium(R) D CPU 2.80GHz
stepping        : 7
cpu MHz         : 3195.157
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 6394.81
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      :               Intel(R) Pentium(R) D CPU 2.80GHz
stepping        : 7
cpu MHz         : 3195.157
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 6390.35
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

---

### Post by PurposeOfReason on 2007-09-19
That still gave me the 2.00GHZ output. :(

---

### Post by dabl on 2007-09-19
I'm wondering if your CPU is "actually" overclocked.  Here's what my overclocked Core 2 Extreme says:

```
dabl@gutsy:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         X6800  @ 2.93GHz
stepping        : 6
cpu MHz         : 3329.995
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6664.30
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         X6800  @ 2.93GHz
stepping        : 6
cpu MHz         : 3329.995
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6660.11
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```

:)

---

### Post by PurposeOfReason on 2007-09-19
I honestly don't get it. See below. Is there some magical setting I'm missing? Asus P5b-E with an Intel E4400.

```
shawn@Desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz
stepping        : 2
cpu MHz         : 2708.146
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5420.78
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4400  @ 2.00GHz
stepping        : 2
cpu MHz         : 2708.146
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 5416.41
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

```

EDIT - I was looking at model name, not cpu MHz. So it's all good?

---

### Post by david_2001 on 2007-09-20
> **PurposeOfReason said:**
> EDIT - I was looking at model name, not cpu MHz. So it's all good?

Yup :-)

---

### Post by dabl on 2007-09-20
Yup.  This:

> cpu MHz         : 2708.146

is all you need to know.

:popcorn:

---

### Post by emshains on 2008-01-03
Either you havent said the BIOS to save&exit, or its just the Cpu MHZ that matters....

Still im  looking for a way to overclock my 3 pentium 500mhz, and it looks like the damn intel motherboard doesnt support anything fun like 2.0 usb, integrated videocard, OVERLOCKING!!!!!

---

### Post by BassKozz on 2008-02-17
:BUMP:

I am having the same issue with my rig (see signature),
here are the results of "cat /proc/cpuinfo":
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 2220.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6664.65
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 2220.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6660.58
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 2220.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 3
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6660.53
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping        : 11
cpu MHz         : 2220.000
cache size      : 4096 KB
physical id     : 0
siblings        : 4
core id         : 2
cpu cores       : 4
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 6660.25
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
```
cpu MHz = 2220mhz :confused:

---

### Post by BassKozz on 2008-02-18
Even Conky is showing 2.22Ghz?
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/conky-ss.jpg[/IMG]
This doesn't make sense because when I boot into my WinXP parition I am showing 3.33ghz
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Server_Rig/OC/3333mhz/th_33ghzprime95blend35hrs.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Server_Rig/OC/3333mhz/33ghzprime95blend35hrs.jpg)

Could it be because I am not stressing the cores and it's in power saving mode (probably)?
If so what can I use to stress the cores in Ubuntu to make sure it's working right?
CPU Benchmarking/Stressing Utilities for Ubuntu?

---

### Post by PurposeOfReason on 2008-02-18
In a terminal type cpufreq-info.

---

### Post by BassKozz on 2008-02-18
> **PurposeOfReason said:**
> In a terminal type cpufreq-info.
Ahhh, much better:
```
user@computer:~$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 2.22 GHz - 3.33 GHz
  available frequency steps: 3.33 GHz, 2.22 GHz
  available cpufreq governors: ondemand, userspace, conservative, powersave, performance
  current policy: frequency should be within 2.22 GHz and 3.33 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.22 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 2.22 GHz - 3.33 GHz
  available frequency steps: 3.33 GHz, 2.22 GHz
  available cpufreq governors: ondemand, userspace, conservative, powersave, performance
  current policy: frequency should be within 2.22 GHz and 3.33 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.22 GHz.
analyzing CPU 2:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 2
  hardware limits: 2.22 GHz - 3.33 GHz
  available frequency steps: 3.33 GHz, 2.22 GHz
  available cpufreq governors: ondemand, userspace, conservative, powersave, performance
  current policy: frequency should be within 2.22 GHz and 3.33 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.22 GHz.
analyzing CPU 3:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 3
  hardware limits: 2.22 GHz - 3.33 GHz
  available frequency steps: 3.33 GHz, 2.22 GHz
  available cpufreq governors: ondemand, userspace, conservative, powersave, performance
  current policy: frequency should be within 2.22 GHz and 3.33 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.22 GHz.

```

Thanks PurposeOfReason:):popcorn:

---

