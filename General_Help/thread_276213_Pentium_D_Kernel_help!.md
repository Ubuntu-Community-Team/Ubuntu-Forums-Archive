---
title: "Pentium D Kernel help!"
date: 2006-10-12
forum: General Help
---

### Post by cmulax on 2006-10-12
i have a pentium d, but i do not know which kind or what kernel i should go for.

this is what cat /proc/cpuinfo gives me:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.40GHz
stepping        : 4
cpu MHz         : 2401.120
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm pni monitor ds_cpl vmx est cid cx16 xtpr lahf_lm
bogomips        : 6810.27

i really would like to optimize ubuntu to run both of my cores, especially since im running beryl.  any advice on what kernel to get would be much appreciated.

thanks in advance!

---

### Post by Paul41 on 2006-10-12
The 686 kernel is for Pentium processors.

---

### Post by Xerix on 2006-10-12
686-smp would allow you to take advantage of both your cores.

---

