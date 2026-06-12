---
title: "AMD dual-core processor showing up as single-core"
date: 2007-04-01
forum: General Help
---

### Post by ceswiedler on 2007-04-01
I just installed the feisty beta on an Asus M2NPV-VM with an Athlon64 X2 4600+. It's gone very smoothly so far, which is great. 

One problem I'm seeing though is that my dual-core processor is only showing up as a single core. Here's my cpuinfo:

```

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 20

```

Is there anything I need to do to enable the kernel to see the second core?

---

### Post by tonym on 2007-04-01
This doesn't seem to be the full cpuinfo -  is it?

What Ubuntu version are you using?  Which kernel?

Regards

Tony

---

### Post by sharke on 2007-04-01
I have Intel core 2 duo and there is nothing in cpuinfo file is empty but both cores are working and show in system monitor.
Regards
Sharke

---

### Post by JohnPhys on 2007-04-01
I'm not sure what kernel the Feisty beta's default to, but have you installed the -smp kernel?  I know in dapper/edgy that needed to occur.

---

### Post by ceswiedler on 2007-04-01
> **tonym said:**
> This doesn't seem to be the full cpuinfo -  is it?

What Ubuntu version are you using?  Which kernel?



That's the entire cpuinfo, yes. I'm running Feisty beta, kernel  2.6.20-13-386. 

I don't see any -smp kernels to install, I think they're all rolled into the -generic kernel package now.

---

### Post by Marsolin on 2007-04-03
I'm having a problem with this as well. I had a dual processor machine and each has Hyper-Threading so I should be showing 4 procs. Instead I'm only showing two. I don't see a separate smp kernel.

---

### Post by JohnPhys on 2007-04-04
Well, you should be running the -generic rather than the -386 kernel, I believe.

---

### Post by Marsolin on 2007-04-05
> **JohnPhys said:**
> Well, you should be running the -generic rather than the -386 kernel, I believe.

I'm already using the generic kernel.

---

### Post by blackrim on 2007-04-05
same problem here

here is my cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 2
cpu MHz         : 2412.385
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4827.65
clflush size    : 64

---

### Post by blackrim on 2007-04-05
fixed it. 
had to open up /boot/grub/menu.lst and move my generic kernel above the i386 (don't know when that got moved up).

---

