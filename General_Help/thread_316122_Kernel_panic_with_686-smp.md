---
title: "Kernel panic with 686-smp"
date: 2006-12-10
forum: General Help
---

### Post by djsroknrol on 2006-12-10
I hava a P-IV 2.8Mhz processor and realized I could run the 686-smp kernel from this:

```
bob@Ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2793.572
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5591.84

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 9
cpu MHz         : 2793.572
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5586.45

```

So I installed the  kernel-headers-2.4.27-2-686-smp and kernel-image-2.4.27-2-686-smp files thru Synaptic, but when I rebooted, I got this message:

> Kernel panic..cannot mount root fs on 08:02

Any ideas as to why this is happening?

---

### Post by djsroknrol on 2006-12-10
Shameless bump...any ideas anyone? Am I missing something?

---

