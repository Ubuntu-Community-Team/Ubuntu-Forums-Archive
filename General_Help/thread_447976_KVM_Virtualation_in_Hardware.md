---
title: "KVM Virtualation in Hardware"
date: 2007-05-18
forum: General Help
---

### Post by scaine on 2007-05-18
I understand that the latest Feisty release supports KVM's hardware-based virtualisation.  I have an AMD-X2 4200 chip which I believe should be compatible.

However, when I installed Feisty a couple of weeks ago, it only recognised one processor on my motherboard and only one core.

I've since realised that my BIOS was out of date and after flashing my BIOS, sure enough, Feisty now sees both processors, and recognises that they are dual-core.  I've posted the output of "cat /proc/cpuinfo" below.

BUT, Feisty has been installed while the installers only saw a single, non-Hyperthreaded processor.  When I run "egrep '^flags.*(vmx|svm)' /proc/cpuinfo" as instructed by the KVM website, there is no output, indicating that my processors are not HT-enabled (they are, in the BIOS - they're set to 5x speed, which is apparently 1Ghz).

Because of this, when I run the "sudo modprobe kvm-amd" command, I get this :
```
FATAL: Error inserting kvm_amd (/lib/modules/2.6.20-15-generic/kernel/drivers/kvm/kvm-amd.ko): Operation not supported
```


So, is there any way to retro-actively tell Feisty to recognise HyperTransport in my processors?

I realise that this is an obscure one, so thanks if anyone can help.


Output of cat /proc/cpuinfo:
```
scaine@Groovy:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
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
bogomips        : 2010.42
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 43
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
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
bogomips        : 2010.42
clflush size    : 64


```

---

### Post by scaine on 2007-05-22
Looks like this one is too complex!

Before I re-install, can anyone at least comment on whether KVM hardware virtualisation is WORTH it?  I'm using VirtualBox at the moment, and it's actually not too bad...

Lemme know, if you can.

---

### Post by kradnz on 2007-11-07
I am having this same problem, did it work with a reinstall? Would upgrading to 7.10 fix the problem?

I'll try it tomorrow, but I am starting to give up hope on getting this to work on this machine: Athlon 64 X2 4400, Asus A8n-Sli motherboard - latest BIOS

---

### Post by kradnz on 2007-11-08
Ok I have now done a fresh reinstall with Ubuntu 7.10.

The SVM flag still doesn't show up int the output of:

cat /proc/cpuinfo

I have the 32-bit version of 7.10 installed. perhaps this is part of the problem.

---

### Post by scaine on 2007-11-13
Nope - sorry.  I'm on Gutsy from a fresh re-install.  My BIOS was flashed and reported that VT technology was available.  But after the (completely clean from CD) install, I still have no result from the cpuinfo command.

I have little use for virtualisation except as a curiosity, so I haven't followed up on this much.  I'll just use VirtualBox for the moment.  It would have been nice to see this hardware acceleration working through.

I hope you have better luck.

---

