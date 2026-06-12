---
title: "1 cpu = 2 cpu ?"
date: 2006-12-31
forum: General Help
---

### Post by CocoAUS on 2006-12-31
I did a clean install of Ubuntu today.  I noticed that after I started Beryl, my tvtime frame rate dropped quite a bit, and the desktop effects were SLOW.  This was never a problem for me before.  I opened up the process manager, and noticed something I've never noticed before--Ubuntu thinks I have two processors!  This must be why PC is so incredibly slow after the new install.

Any idea how to fix this?  Or what caused this?

---

### Post by CocoAUS on 2006-12-31
I have a single Intel Pentium 4 3.0GHZ processor with HT.  I did a sudo cat /proc/cpuinfo, and I got:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 2992.866
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
bogomips        : 5991.13

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 2992.866
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
bogomips        : 5985.44
```

---

### Post by iamhugeinjapan on 2007-01-01
Your processer has hyperthreading turned on, so it's virtually two cpus. This is why Ubuntu shows you that.

---

