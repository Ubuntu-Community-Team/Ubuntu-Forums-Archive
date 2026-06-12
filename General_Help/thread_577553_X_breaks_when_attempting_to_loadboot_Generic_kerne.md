---
title: "X breaks when attempting to load/boot Generic kernels."
date: 2007-10-16
forum: General Help
---

### Post by Faer on 2007-10-16
I'm extremely new to Linux, so please, if what I say makes little sense to you, or is common knowledge, feel free to point it out and teach me the proper terminology. On the same note, if there's some sort of information I should be providing that I am not, just let me know, and I'll obtain (and then post) it as quick as I can.

My cpuinfo:

```
user@user-LINUX:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 1800.000
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
bogomips        : 3619.58
clflush size    : 64

```

I'm currently running the 2.6.20-16-386 kernel for Feisty Fawn. Because, apparently, 386 doesn't have SMP enabled (or something of that nature; the problem that brought me to this point was that my system isn't recognizing my second CPU core), I obtained the 2.6.20.16-generic package, rebooted, attempted to load using the new generic rather than the 386, and was promtly greeted by the message that my xorf was borked and I should reconfigure it. So I did pdkg-reconfigure xserver-xorg, essentially chose all the default options, and attempted to startx... Still no-go. The same happened with the .15-generic package, which I apparently already had installed somehow.

I've Googled around for about half a day now, and flipped through the forums for a while, and haven't found anything that helped me (either because it wasn't working for me, or I just plain didn't understand what was being said). I'm really stumped here, and don't have the foggiest idea where to start in order to fix either problem.

I'd really appreciate any insight you guys could give me on the matter.

---

