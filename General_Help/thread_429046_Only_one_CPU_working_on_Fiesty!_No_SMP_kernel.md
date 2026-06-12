---
title: "Only one CPU working on Fiesty! No SMP kernel"
date: 2007-04-30
forum: General Help
---

### Post by lancest on 2007-04-30
Running dual core laptop. Only one CPU working after fresh install!!!
What gives?  Had Fiesty installed before no problem.
 uname -a
Linux CalLinux-laptop 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux  (no SMP)

lance@CalLinux-laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 996.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3661.62
clflush size    : 64

This guy says: 
the 386 kernel doesn’t support dual core/SMP
[http://www.economysizegeek.com/category/linux/ubuntu/](http://www.economysizegeek.com/category/linux/ubuntu/)

---

### Post by tgm4883 on 2007-04-30
why are you running the i386 kernel and not the generic kernel (which has SMP support)?

---

### Post by lancest on 2007-04-30
Because I was given no choice when I installed Fiesty and on 2 previous Fiesty dual core installs there was no problem. Is this kind of a bug? Which kernel should I choose from Synaptic? Is there an install method? No experience choosing a kernel before.

---

### Post by tgm4883 on 2007-05-01
hmm, the generic kernel should be default.

:EDIT:

Is this a fresh install or an upgrade?

---

### Post by lancest on 2007-05-01
It is an upgrade (from Fiesty Beta). In Synaptic- linux-generic (complete Linux kernel) shows not installed. Should I chance it?
Otherwise back to fresh install.

---

### Post by tgm4883 on 2007-05-01
id back up just to be safe, then install linux-generic.  That will give you the latest generic kernel and SMP support.  If for some strange reason that doesn't work you can still select your old kernel from grub and boot that.  If for some stranger reason that doesn't work either, then you have a backup of your data and were going to reinstall anyway.

Heres my uname -a on my core 2 duo
> 
thomas@poseidon:~$ uname -a
Linux poseidon 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

---

