---
title: "Athlon dual core only reporting 1 processor"
date: 2008-01-15
forum: General Help
---

### Post by dlynch912 on 2008-01-15
Hello all.

I recently bought an Acer Aspire M5100 Desktop machine with an AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ with 1G of ram and installed Gutsy 32bit.  For some reason gutsy is only recognizing 1 of the 2 cores.  I've disabled AMD "Cool 'n' Quiet" in the bios and I'm running the generic kernel.

Does anyone know why it's only recognizing 1 processor and how I can resolve this issue? Thanks in advance for all your help.

~Dave

Here's some output:

dave@acheron:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping        : 1
cpu MHz         : 2294.384
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips        : 4737.70
clflush size    : 64

dave@acheron:~$ uname -a
Linux acheron 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

dave@acheron:~$ dmesg | grep -i proc
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] Detected 2294.384 MHz processor.
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.388000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ stepping 01
[    0.388000] Booting processor 1/1 eip 3000
[    5.536000] Total of 1 processors activated (4737.70 BogoMIPS).
[   24.632000] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (version 2.00.00)
[   25.452000] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (version 2.00.00)

---

### Post by jeffus_il on 2008-01-15
See this thread:
[http://ubuntuforums.org/showthread.php?t=655812&highlight=dual+core+one+processor](http://ubuntuforums.org/showthread.php?t=655812&highlight=dual+core+one+processor)

---

