---
title: "cpuinfo showed 2 processor but top showing only 1"
date: 2007-12-04
forum: General Help
---

### Post by tomcatf14 on 2007-12-04
/proc/cpuinfo

```
cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 3
cpu MHz         : 2800.311
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid
bogomips        : 5606.68

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping        : 3
cpu MHz         : 2800.311
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid
bogomips        : 5600.43
```

In top, i doesn't show 2 processors? Why?

---

### Post by killabc on 2007-12-04
Press the number 1 on numeric keybord to show 2 processors..

---

### Post by tomcatf14 on 2007-12-04
Wow...Magical "1"...hahaha
Is it the same for Quad Core?

---

### Post by tomcatf14 on 2007-12-04
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.20GHz
stepping        : 5
cpu MHz         : 3200.038
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl est cid cx16 xtpr lahf_lm
bogomips        : 6406.10

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Pentium(R) D CPU 3.20GHz
stepping        : 5
cpu MHz         : 3200.038
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl est cid cx16 xtpr lahf_lm
bogomips        : 6400.05
```
This is a dual core, why it is showing the following?

core id         : 255
cpu cores       : 1

---

### Post by der_joachim on 2007-12-05
Are you sure that you are running the right kernel? Do a *uname -r* and the output should be something like ```

2.6.22-generic

```

If it **is** the generic kernel, there may be some other problem.

---

