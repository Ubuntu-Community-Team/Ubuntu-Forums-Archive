---
title: "Why do I have 2 CPU's"
date: 2008-02-04
forum: General Help
---

### Post by adn258 on 2008-02-04
I only have one CPU I thought even though it shows two.  I remember on windows it only showed one CPU???

---

### Post by jan quark on 2008-02-04
run 

```
lshw
```

and look at the cpu output

---

### Post by DrMega on 2008-02-04
> **adn258 said:**
> I only have one CPU I thought even though it shows two.  I remember on windows it only showed one CPU???

What CPU is it? Is it dual core?

---

### Post by cbtengr on 2008-02-04
> **DrMega said:**
> What CPU is it? Is it dual core?

Older PCwith Hyperthreading?

---

### Post by spec-chum on 2008-02-04
> **cbtengr said:**
> Older PCwith Hyperthreading?

Same as mine.  A hyperthreaded processor shows up as two CPUs

---

### Post by DrMega on 2008-02-04
Have a look at this:

[http://en.wikipedia.org/wiki/Hyper-threading](http://en.wikipedia.org/wiki/Hyper-threading)

I didn't know that, you got me thinking because my old Pentium 4 at work shows as 2 CPUs and I thought it was because it was dual core, until I remembered it is getting on in years so probably isn't.

---

### Post by adn258 on 2008-02-05
here's what is says about th CPU

 *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical

---

### Post by Zwack on 2008-02-05
Given that it shows two "logical" CPUs then you have hyperthreading turned on...

Confusing, but that's what it is...

In /proc/cpuinfo I think you'll find that it reports multiple siblings on each processor.

Z.

---

### Post by dicecca112 on 2008-02-05
> **Zwack said:**
> Given that it shows two "logical" CPUs then you have hyperthreading turned on...
 
Confusing, but that's what it is...
 
In /proc/cpuinfo I think you'll find that it reports multiple siblings on each processor.
 
Z.
 
No hyperthread is not on, it hasn't be on Intel Processers since the p4 Days. OP you have a Core 2 Duo. Basically its a single Processor with 2 cores. Essential 2 CPUs in on epackage
 
with windows, by default task manager shows one graph for both CPUs, you have the option to show 2 graphs **OR **the wrong APCI is installed in Windows and windows is not taking advantage of the dual core processor.  I assume this is a laptop, who makes the laptop (ie model and brand)

---

### Post by adn258 on 2008-02-05
> **dicecca112 said:**
> No hyperthread is not on, it hasn't be on Intel Processers since the p4 Days. OP you have a Core 2 Duo. Basically its a single Processor with 2 cores. Essential 2 CPUs in on epackage
 
with windows, by default task manager shows one graph for both CPUs, you have the option to show 2 graphs **OR **the wrong APCI is installed in Windows and windows is not taking advantage of the dual core processor.  I assume this is a laptop, who makes the laptop (ie model and brand)

I think your right BTW and it's an HP dv6000 and I appreciate it man :).

---

