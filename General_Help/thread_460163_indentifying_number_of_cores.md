---
title: "indentifying number of cores"
date: 2007-05-31
forum: General Help
---

### Post by jdrodrig on 2007-05-31
Hi,

I run some fortran codes in a four Opteron 275 machine (8 cores), but I am not sure I am fully using the 8 cores. No matter I set the number of threads to 4 or 8, I get "top" reporting my process as using 400% of CPU. Is there a way to know if I am using the eight cores from top or some similar reporting tool? is top's cpu column reporting per die or per core?

uname -a gives
Linux *(removed) 2.6.9-42.0.10.ELsmp #1 SMP Fri Feb 16 17:13:42 EST 2007 x86_64 x86_64 x86_64 GNU/Linux

Thanks,
PS In case you are wondering, I use OpenMP directives in my fortran code. I am almost certain the cause is not a programming mistake.

---

### Post by der_joachim on 2007-05-31
Here's an easy way: in a console, just run the program 'top'. You can view all CPUs by pressing '1'. That's all. :)

---

### Post by dbott67 on 2007-05-31
> **der_joachim said:**
> Here's an easy way: in a console, just run the program 'top'. You can view all CPUs by pressing '1'. That's all. :)

That's cool... you can also type:

```
dbott@feisty:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 1.80GHz
stepping        : 4
cpu MHz         : 1816.305
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
bogomips        : 3636.07
clflush size    : 64

```

You should see every instance of CPU detected.  My desktop is only a single CPU (Processor: 0); a multi-core system will display info on all CPUs.

-Dave

---

### Post by jdrodrig on 2007-05-31
thanks, the "1" in top gave me more info...I noticed that if I specify 2 threads (setenv PARALLEL, setenv OMP_NUM_THREADS), top shows 2 CPUs at 100%..... I guess it is a stupid question, but does this mean the scheduler is allocating each tread to cores in different CPUs? why not allocating it to two cores in the same CPU? if only one core in a CPU were used, would top show 50% for that CPU? is there a per core usage % monitor available somewhere? 

from cat /proc/cpuinfo I got:

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 33
model name	: Dual Core AMD Opteron(tm) Processor 275
stepping	: 2
cpu MHz		: 996.160
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext lm 3dnowext 3dnow pni
bogomips	: 3585.36
TLB size	: 1088 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 33
model name	: Dual Core AMD Opteron(tm) Processor 275
stepping	: 2
cpu MHz		: 996.160
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext lm 3dnowext 3dnow pni
bogomips	: 3585.36
TLB size	: 1088 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 33
model name	: Dual Core AMD Opteron(tm) Processor 275
stepping	: 2
cpu MHz		: 996.160
cache size	: 1024 KB
physical id	: 1
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext lm 3dnowext 3dnow pni
bogomips	: 1991.87
TLB size	: 1088 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 33
model name	: Dual Core AMD Opteron(tm) Processor 275
stepping	: 2
cpu MHz		: 996.160
cache size	: 1024 KB
physical id	: 1
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext lm 3dnowext 3dnow pni
bogomips	: 1991.87
TLB size	: 1088 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

