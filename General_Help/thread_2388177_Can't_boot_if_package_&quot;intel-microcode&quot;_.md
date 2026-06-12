---
title: "Can't boot if package &quot;intel-microcode&quot; is installed"
date: 2018-03-29
forum: General Help
---

### Post by bryantj247 on 2018-03-29
Edit: This bug is being discuessed at [https://bugs.launchpad.net/ubuntu/artful/+source/linux/+bug/1759920](https://bugs.launchpad.net/ubuntu/artful/+source/linux/+bug/1759920).

Today I noticed an update to the intel-micocode package. When I restarted the computer, it didn't make it to the login screen. The previous kernel worked, so I used it and removed intel-microcode, which stopped the newer kernel from crashing. I reinstalled it just to be sure, and it crashed again.

Should I just leave out the intel-microcode package and not worry about it? When I remove intel-microcode and reboot, I'm running microcode 0x28 instead of 0x29.

I'm running Ubuntu 17.10, and linux-image-4.13.0-37-generic is the kernel that was failing.

Here's the /proc/cpuinfo for one of the threads (from linux-image-4.13.0-36-generic with intel-microcode installed) :

[FONT=courier new]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 42
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
stepping        : 7
microcode       : 0x29
cpu MHz         : 3392.298
cache size      : 8192 KB
physical id     : 0
siblings        : 8
core id         : 0
cpu cores       : 4
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm epb pti retpoline tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts
bugs            : cpu_meltdown spectre_v1 spectre_v2
bogomips        : 6784.59
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:
[/FONT]

---

