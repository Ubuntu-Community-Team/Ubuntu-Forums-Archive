---
title: "Half of my Core2Duo not showing up - Feisty"
date: 2007-09-23
forum: General Help
---

### Post by Mike Graham on 2007-09-23
I have Feisty installed on a system with a Core2Duo (E4300). I noticed a small performance drop recently. Investigating a bit, I cannot seem to find half of my CPU.  

My processor used to show up as two CPUs in HAL Device Manager, Gnome System Monitor as two, but now only a single is listed. Here is a printout of my /proc/cpuinfo (this is it, the whole shebang). I was told a [screenshot](http://img98.imageshack.us/my.php?image=cpuinfowy6.png) would boost my believability.


```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping        : 2
cpu MHz         : 1795.556
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3593.84
clflush size    : 64

```

My uneducated speculation is that something happened at some point messing with getting the nVidia proprietary drivers to work right.

---

