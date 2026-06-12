---
title: "Question about dual core AMD"
date: 2007-06-05
forum: General Help
---

### Post by raffytaffy on 2007-06-05
I was discussing with a friend my dual core that i rescently purchased. its a AMD Athlon(tm) 64 X2 Dual Core Processor 3600+

My ubuntu shows it as 

raf@equinox2:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping        : 2
cpu MHz         : 1000.000
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 2010.35
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping        : 2
cpu MHz         : 1000.000
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 2010.35
clflush size    : 64

so 1ghz per core. My friend is telling me since its dual core each core should be 2ghz. So that would mean something is wrong with my isntall..or is my friend wrong? please help:( im worried here

---

### Post by steeleyuk on 2007-06-05
Your CPU may have Cool 'n' Quiet enabled which reduces the CPU frequency when the load is low. This makes for a quieter fan speed, lower power consumption and less heat. You can disable it in the BIOS if necessary.

---

### Post by Znupi on 2007-06-05
They usually put the "3600+" in the name just to confuse (fool) you. I think Ubuntu is right, both your CPU's are at 1Ghz. For me, it shows it right, I have Pentium DualCore, each one being at 2.80Ghz (so a total of 5.60 :D). So, my guess is that Ubuntu's right. Ask the dealers from where you bought your CPU.

---

### Post by steeleyuk on 2007-06-05
The CPU speed is per core, so a 3600+ should be 2GHz per core...

---

### Post by lamadredelsapo on 2007-06-05
Steeleyuk is right, the AMD Athlon X2 3600+ CPU is 2GHz per core, but as Cool'n'Quiet is enabled the processor speed is scaled down to 1GHz to save energy.

Znupi, you obviously have very little understanding of modern processors, so before trying to give advice, please go and study a little about them.

RaffyTaffy, don't worry about it, the processor speed would be scaled up when needed (such as video encoding)

---

### Post by Znupi on 2007-06-05
> **lamadredelsapo said:**
> Znupi, you obviously have very little understanding of modern processors, so before trying to give advice, please go and study a little about them.
That's what a guy with experience in this domain told me. Hmm... maybe he was wrong :|. (I'm not being sarcastic, I said that because I thought that guy was right... I really do have little knowledge about CPUs)

---

### Post by raffytaffy on 2007-06-05
yeah ...i disabled cool and quiet and its goin @ 2ghz per core now. slightly warmed temps..but still well within range.

---

### Post by daniel of sarnia on 2007-06-05
You might want to turn it back on though, you're just using twice the electricity when you don't even need to. When you do need all your processor it automatically will scale back up to full power so I don't think there is any good reason to turn scaling off. You should also in theory get a longer life out of your cpu by it clocking down when full power is not needed.

---

### Post by raffytaffy on 2007-06-06
i do a lot of music editing / remastering. Ever since i switched off the cool and quiet my programs run faster and are more responsive. This processor only needs to last me till Christmas when i will buy myself a more powerfull 6000 fx dual core or better.

---

### Post by steeleyuk on 2007-06-06
Just think of all the money you'll save with less electricity used... :)

---

