---
title: "AMD Athlon(tm) 64 X2 Dual Core Processor 5200+"
date: 2007-04-30
forum: General Help
---

### Post by justin on 2007-04-30
Hi, I am using the processor in the title, and it's suppossed to be 2.6 ghz, but when I run
```

cat /proc/cpuinfo
```

I get this output:

```
justin@rain:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 67
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips	: 2011.05
clflush size	: 64

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 67
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips	: 2011.05
clflush size	: 64
```

Shouldn't "cpu Mhz" be 2600.00 instead of 1000.0?

---

### Post by justin on 2007-04-30
Is it possible the problem is the fact I am running 32 bit feisty instead of 64 bit?

---

### Post by srt4play on 2007-04-30
Laptop or desktop?

---

### Post by justin on 2007-04-30
Desktop

Asus M2N Motherboard

---

### Post by justin on 2007-04-30
BUMP for sanity. I'm having trouble finding information on such a thing.

---

### Post by justin on 2007-04-30
I was thinking of trying this:

```
sudo apt-get install linux-k7
```

Might that solve my issue?

---

### Post by m.musashi on 2007-04-30
The CPU scales depending on demand. I have a 2.4 GHz 4800 and it also tells me 1000mhz with
```
cat /proc/cpuinfo
```
Run a burnin app or something that stresses your cpu and see what happens. You could also turn off frequency scaling (in the BIOS I think but there may be a way to use governors like on a laptop). I doubt there is anything wrong with the CPU.

EDIT:
With cpu burn running I get this
```
jim@feisty:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 2
cpu MHz         : 2400.000
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
bogomips        : 4826.22
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
stepping        : 2
cpu MHz         : 2400.000
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
bogomips        : 4826.22
clflush size    : 64
```
It now shows 2400mhz.

---

