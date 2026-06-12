---
title: "Upgraded CPU to Dual Core"
date: 2008-05-11
forum: General Help
---

### Post by stealth17 on 2008-05-11
I just upgrade my Opteron 150 single core to a Opteron 165 dual core. I booted up and noticed right away that my gKrellM was showing two CPUs now. Here is the output of my uname: Linux stealth17-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Do I have to upgrade my kernel? I see that the kernel says SMP, by it said that when I had the single core too....

Anything else I should know about the dual core? Is there a way to set affinity?

Thanks,
Jordan

---

### Post by HunterThomson on 2008-05-11
Ya, you can enable multi threading now and you can install the 64bit OS.

---

### Post by ruzkie on 2008-05-11
no need

---

### Post by stealth17 on 2008-05-11
> **HunterThomson said:**
> Ya, you can enable multi threading now and you can install the 64bit OS.

Enable multi threading?

I don't want to install the 64bit OS, I've played with it numerous times and yes I do love it and it is faster and such, but this I really need ultimate compatibility for work... plus I only have 2gb of memory so I wouldn't be gaining memory support either.

---

### Post by HunterThomson on 2008-05-11
> **stealth17 said:**
> Enable multi threading?

I don't want to install the 64bit OS, I've played with it numerous times and yes I do love it and it is faster and such, but this I really need ultimate compatibility for work... plus I only have 2gb of memory so I wouldn't be gaining memory support either.

Yes, as far as I know you would have to recompile the kernel to do this but it mite be able to be dynamicly changed now.

---

### Post by stealth17 on 2008-05-11
> **HunterThomson said:**
> Yes, as far as I know you would have to recompile the kernel to do this but it mite be able to be dynamicly changed now.

Even though my kernel already says SMP?

---

### Post by sdennie on 2008-05-11
If /proc/cpuinfo is showing 2 cpus, you should be fine.  The SMP part of "uname -a" just shows how your kernel was compiled so, the fact that it said SMP even when you had a single CPU is normal.  There really isn't much more to know about multi-cpu systems.  I wouldn't worry about processor affinity unless you know that you really need it.

---

### Post by stealth17 on 2008-05-11
> **vor said:**
> If /proc/cpuinfo is showing 2 cpus, you should be fine.  The SMP part of "uname -a" just shows how your kernel was compiled so, the fact that it said SMP even when you had a single CPU is normal.  There really isn't much more to know about multi-cpu systems.  I wouldn't worry about processor affinity unless you know that you really need it.

Yeah it's showing both:

```
stealth17@stealth17-desktop:~/superpi$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165   
stepping        : 2
cpu MHz         : 2430.704
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4864.41
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : Dual Core AMD Opteron(tm) Processor 165   
stepping        : 2
cpu MHz         : 2430.704
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4861.70
clflush size    : 64

```

---

### Post by sdennie on 2008-05-11
Based on the "uname -a" and "/proc/cpuinfo", I'd say you are all set.  No changes should be needed.

---

### Post by HunterThomson on 2008-05-11
the smp kernel is used for both single and duel core processor. I am not an expert on this. If it were me I would reinstall and install the 64bit OS to make full use of the duel core processor you have now. This would be a vary ez and painless data loss less process if you had a separate partition for /home. But, you don't have to do anything.

---

### Post by bingoUV on 2008-05-11
> **stealth17 said:**
> 
Anything else I should know about the dual core? Is there a way to set affinity?

Thanks,
Jordan

To set affinity of process with PID 12345 to core 0, 
```

taskset 0x00000001 -p 12345

```

For details, 
```

man taskset

```

I hope this will work as default Ubuntu kernel should be taskset enabled by default. I could be wrong though.

---

### Post by stealth17 on 2008-05-11
Is Firefox 3 Beta 4 multithreaded? It seems like it when looking at the CPU graphs.

---

