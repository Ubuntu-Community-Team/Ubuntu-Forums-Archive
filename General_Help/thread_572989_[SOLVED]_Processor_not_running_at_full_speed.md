---
title: "[SOLVED] Processor not running at full speed?"
date: 2007-10-11
forum: General Help
---

### Post by perlluver on 2007-10-11
In KInfoCenter it says 1000Mhz but it is a 2Ghz processor, is this normal, or does it need fixed?

edit: it is an AMD Sempron 3400+ if that helps.

---

### Post by thirddeep on 2007-10-11
I have no idea what KInfoCenter is, but do the following :
```
cat /proc/cpuinfo
```

and post the output..

Thd.

---

### Post by perlluver on 2007-10-11
This is the output...

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 44
model name      : AMD Sempron(tm) Processor 3400+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips        : 2011.09
clflush size    : 64

---

### Post by thirddeep on 2007-10-11
Interesting ... you are right, it's running at 1GHz.  I believe AMD have a list that you can compare the FLAGS & CPU FAMILY & MODEL & STEPPING to see if you really do have the right CPU inside there.

Or perhaps pull the heat sink of and look.

Thd.

---

### Post by LaDeDa on 2007-10-11
I run a 3700 on a WinXP machine.  Installing, and invoking, the AMD processor program "Cool & Quiet" reduces the CPU out put to "997mhz".  By chance, do you have "Cool & Quiet" ??

---

### Post by perlluver on 2007-10-11
No if it does I didn't see it.  I checked the BIOS but didn't see anything pertaining to Cool & Quiet.

---

### Post by tszanon on 2007-10-11
If Cool n Quiet is running, then that's the reason. Does anyone here remember the name of the process for CnQ?

---

### Post by thirddeep on 2007-10-11
Cool & Quiet will not be noted in the BIOS.

IIRC, you can get the speed of the CPU in the BIOS (if it's a good BIOS).

Thd.

---

### Post by James79 on 2007-10-11
That's definetly CnQ in action. It's enabled by default if your cpu/motherboard support it.

You have an AM2 board, right?

By the way, this is nothing to worry about. I find it's a very nice and reliable feature :)

---

### Post by perlluver on 2007-10-11
Ok just wanted to make sure it wasn't messed up or anything.  Thanks for all the help! !:)

---

