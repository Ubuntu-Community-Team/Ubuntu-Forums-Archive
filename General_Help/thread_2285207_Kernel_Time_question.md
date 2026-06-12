---
title: "Kernel Time question"
date: 2015-07-03
forum: General Help
---

### Post by linuxnz123 on 2015-07-03
In my dmesg i get following lines:

```

dmesg|grep -i kvm
[  712.202195] kvm: SMP vm created on host with unstable TSC; guest TSC will not be reliable
[  712.458496] kvm: zapping shadow pages for mmio generation wraparound

```


```

cat /sys/devices/system/clocksource/clocksource0/available_clocksource 
hpet acpi_pm 

```

```

cat /sys/devices/system/clocksource/clocksource0/current_clocksource 
hpet

```

How do i fix this use of unstable TSC.

My processor is:
```

rocessor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 62
model name      : Intel(R) Xeon(R) CPU E5-1650 v2 @ 3.50GHz
stepping        : 4
microcode       : 0x428
cpu MHz         : 1282.421
cache size      : 12288 KB
physical id     : 0
siblings        : 12
core id         : 0
cpu cores       : 6
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt
bugs            :
bogomips        : 6983.22
clflush size    : 64
cache_alignment : 64
address sizes   : 46 bits physical, 48 bits virtual
power management:

```

---

### Post by sandyd on 2015-07-04
Most people either use kvm-clock or NTP, or TSC if CPU supports it.

Host node will need [kvm-clock enabled]("http://www.linux-kvm.org/page/KVMClock")

If kvm-clock is not enabled, then use NTP. NTP may have a bit of skew due to server closeness, but is negligible.

Your CPU does not have the constant_tsc flag, as a result, TSC cannot be used.

---

### Post by linuxnz123 on 2015-07-04
How do I enable kvm-clock in my kubuntu 15.04?

Thanks

---

