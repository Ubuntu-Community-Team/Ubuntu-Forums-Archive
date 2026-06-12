---
title: "Cpus at 1995.083 instead of 2 ghz?"
date: 2007-01-27
forum: General Help
---

### Post by no24 on 2007-01-27
sorry if this is a dumb question, but I was initially getting 1 ghz on each processor, and after following instructions to go from "half" to "full" speed it's at 1995.083 instead of 2ghz. Is this right?

cat /proc/cpuinfo says

```

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 1995.083
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
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3990.20

```

thanks!

---

### Post by AirRaven on 2007-01-27
CPU Clock Speeds aren't totally constant- you'll find that they fluctuate slightly. 

5MHz isn't much to worry about, by any standards, anyway.

---

### Post by no24 on 2007-01-27
yea.. it just seems to be consistently like this. it doesnt fluctuate when I check it and has been this way the past few days?

---

### Post by r4ik on 2007-01-27
Here is mine,

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      : Intel(R) Celeron(R) D CPU 3.20GHz
stepping        : 4
cpu MHz         : 3192.963
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl cid cx16 xtpr lahf_lm
bogomips        : 6390.50

not 3.20 also.

---

### Post by chalex on 2007-01-27
Yes, this is fine.  Here's mine:
> model name      : AMD Sempron(tm) Processor 3400+
stepping        : 2
cpu MHz         : 1990.316


---

### Post by Malac on 2007-01-27
Most chip MHz, like disk and memory MB are calculated on a "fuzzy" basis and for chips this usually means rounding up.
You buy a Pentium 2GHz or 4GHz not a Pentium 1.974GHz or 3.942 GHz.
The former sounds snappier, takes up a lot less print and sounds faster.

For the same reasons shops sell stuff at #9.99 instead of #10-00. For want of #0.01 they make more sales as #10.00 "feels" more than #9.99 than it should.

---

### Post by no24 on 2007-01-28
cool thanks.. sorry for being a newb haha.

---

