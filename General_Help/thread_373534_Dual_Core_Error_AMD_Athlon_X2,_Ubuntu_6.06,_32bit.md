---
title: "Dual Core Error: AMD Athlon X2, Ubuntu 6.06, 32bit"
date: 2007-03-01
forum: General Help
---

### Post by areseapea on 2007-03-01
First time poster here.  Had a look around the forums, tried various solutions there, but none seem to work.

I have a Dell Dimension E521, with and AMD Athlon 64 X2 Dual Core Processor 4200+.  I'm running 6.06 32-bit, as that was what I installed shortly after getting the machine, and don't really want to have to re-setup all my programs with Ubuntu 64-bit!

Ubuntu is currently only recognising 1 core.  I have installed the k7 kernel (uname -a: Linux Rivendell 2.6.15-28-k7 #1 SMP PREEMPT Thu Feb 1 16:36:09 UTC 2007 i686 GNU/Linux) to no avail.  cat /proc/cpuinfo looks like this:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 2205.024
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy
bogomips        : 2007.21

When I look at dmesg, I can see this near the top:

[17179569.908000] ACPI: Looking for DSDT ... not found!
[17179569.916000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[17179569.916000] SMP alternatives: switching to SMP code
[17179569.916000] Booting processor 1/1 eip 3000
[17179575.316000] Not responding.
[17179575.316000] Inquiring remote APIC #1...
[17179575.316000] ... APIC #1 ID: 01000000
[17179575.316000] ... APIC #1 VERSION: 80050010
[17179575.316000] ... APIC #1 SPIV: 000000ff
[17179575.316000] CPU #1 not responding - cannot use it.
[17179575.316000] Total of 1 processors activated (4415.88 BogoMIPS).

I can post the whole dmesg if that helps!  I hope I haven't duplicated a post.  Any help would be great.  Have really loved Ubuntu, glad to lose Windows, but I don't want to be only using half my machine!

---

### Post by play0r on 2007-03-01
try using the boot option:

```
acpi=off
```

if you haven't already. hopefully that will sort you out. 
i'm not really familiar with amd64/dual core setups, i'm still rocking a 1.1ghz duron oc'd to 1.25ghz using the pencil trick to unlock the multiplier. :-# 

ez,
play0r

---

### Post by Maestro23 on 2007-03-01
I run dual-core AMD as well w/32-bit Edgy 6.10.  Here' mine cat/proc/cpuinfo:

> processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
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
bogomips        : 2007.32

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
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
bogomips        : 2007.32



---

### Post by areseapea on 2007-03-02
Thanks guys!

I ran up the machine with the k7 kernel, with the following added to the kernel line in grub:
noapic acpi=noirq

This has done the trick.  I now have both cores and the machine is running much faster!

I also re-flashed the BIOS with version 1.1.4, which sorted out all the problems with mouse and keyboard.

All is well!

---

### Post by sorceror on 2007-03-30
> **areseapea said:**
> Ubuntu is currently only recognising 1 core.  I have installed the k7 kernel (uname -a: Linux Rivendell 2.6.15-28-k7 #1 SMP PREEMPT Thu Feb 1 16:36:09 UTC 2007 i686 GNU/Linux) to no avail.

I've got the same problem, but it's a dual-CPU 32-bit Athlon system. Same kernel, and Ubuntu 6.06. It used to recognize both CPUs, but today I noticed that copying a DVD took 100% CPU when it used to take 50%. I checked and sure enough, only one CPU listed in /proc/cpu.

I'll try backing up a kernel rev and see if that helps.

---

