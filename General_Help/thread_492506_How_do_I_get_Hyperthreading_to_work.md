---
title: "How do I get Hyperthreading to work"
date: 2007-07-04
forum: General Help
---

### Post by herbster on 2007-07-04
Or does it already? I have a P4 with HT, how do I tell if it's "working" ?

Here's my cat /proc/cpuinfo:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping        : 5
cpu MHz         : 3400.351
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6808.80
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.40GHz
stepping        : 5
cpu MHz         : 3400.351
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6800.18
clflush size    : 64
```

I also did:

```
sudo apt-get install linux-686-smp
```

Anyone ?

---

### Post by mbeierl on 2007-07-04
Do you actually have 2 cpus?  If not, then the fact that two are showing up under /proc/cpuinfo means your hyperthreaded chip is working.

Boot into the non-smp kernel and you should see the 2nd cpu go away.

---

### Post by herbster on 2007-07-05
mbeierl,

Thanks! No I have a regular P4 w/HT, good to know she's chuggin' along :)

---

