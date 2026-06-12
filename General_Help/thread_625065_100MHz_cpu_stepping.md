---
title: "100MHz cpu stepping"
date: 2007-11-27
forum: General Help
---

### Post by dragon76 on 2007-11-27
I am trying to find out how to get cpu stepping in 100MHz increments. I have tried powernowd with the -s 100000 option but I still only get 3 steps. My processor supports 100MHz steps as shown by /proc/cpuinfo

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 104
model name      : AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53
stepping        : 1
cpu MHz         : 800.000
cache size      : 256 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips        : 1608.72
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 104
model name      : AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53
stepping        : 1
cpu MHz         : 800.000
cache size      : 256 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips        : 1608.72
clflush size    : 64

Does anyone have any ideas?

Thanks in advance.

---

