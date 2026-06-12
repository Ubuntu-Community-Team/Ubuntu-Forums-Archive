---
title: "Help with Overclocked CPU"
date: 2008-06-10
forum: General Help
---

### Post by jrharvey on 2008-06-10
Ok so I have an overclocked Core2 Quad Q6600 @ 3.0ghz and windows reads this fine. Ive done many test in windows and it is perfectly stable and claims a legit 3.0ghz speed with CPU-Z. Now ubuntu doesnt seem to read the overclock at all. In conky it reads 2.4 max (the origional speed b4 overclock). So im lost here. Does overclocking only work with windows? Could it be the way the 2 different Kernels control the CPU? I guess im just lost here.

---

### Post by jrharvey on 2008-06-10
Wow, does nobody know this? Someone else out there has to have overclocked their machine.

---

### Post by Titan8990 on 2008-06-10
Overclocking is something typically done by gamers. Linux is not a gaming OS. I am sure there are apps out there that will do what you are looking for but a Windows platform there are a ton of these tools as you have seen.

Your BIOS controls you oc. You did OC in the BIOS didn't you? It is universal. You can use lmsensor to monitor your temps if you need to but I assure you that if you OCed in your BIOS (**you should not overclock any other way**) then your CPU is overclocked no matter what software OS you are running.

---

### Post by jrharvey on 2008-06-10
Yes you are correct with everything you just said. Unfortunately this whole discussion started because I cannot read my temps in ubuntu. Its not the Motherboard as windows sees the temps just fine. I have LMsensors installed but its still a no go. Any other sugguestions?

---

### Post by jrharvey on 2008-06-10
BTW, i am not a gamer but the programs i use both linux and windows HOG the CPU.

---

### Post by jrharvey on 2008-06-10
bump

---

### Post by bollix47 on 2008-06-10
If you open a terminal and type:

```
cat /proc/cpuinfo
```

what does it say for cpu MHz?

---

### Post by jrharvey on 2008-06-10
it says 1.6 ghz but im assuming its the down stepping used to save power when not in use. It will change from a multiplyer of 9 to 6 but that still makes it a 2.4 when added all up. This is weird. Like i said, is it possible that the linux kernel reacts different to the processor than the windows kernel? I wonder if it even counts as being overclocked in ubuntu. Is it possible that Linux overides the BIOS?

---

### Post by gm04030276 on 2008-06-10
The overclocking does work. Its a hardware thing done with bios settings to the motherboard. It happens before the OS even loads. Unless you used some windows app to do it in which case i'm not sure but I have several overclocked linux boxes, 2 Q6600's in ASUS P5K MB's at 3.4GHz. I know they are over clocked because they run my folding at home cores faster and produce alot more heat than when they weren't overclocked! Ill try running that command and see what it says for clock speed tho! 

It shows it as 2394 MHz but i'm still sure its OC'd!

Also lm_sensors takes a bit of poking to get it to work. Just keep trying!

Wait, I just remembered the system I ran that command on is currently down clocked for the moment...ill try in on the other one!

...
ok, my OC'd E6700 does show as running at 3.6 in /proc/cupinfo but my Q6600 shows as above in another P5k system that i'm sure is running at 2.6...hmm. idk

---

### Post by bollix47 on 2008-06-10
Mine shows:

cpu MHz		: 3005.553

I *think* I disabled Speedstep in the bios and I know I stopped CPU Frequency manager under Administration > Services.

Since I too run F@H 24/7 I had no need for the cpu to slow down. ;)

Running a Q6600 on a P5K.

---

### Post by jrharvey on 2008-06-10
```
jrharvey@jrharvey-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 6003.57
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5999.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5999.33
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5999.34
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by jrharvey on 2008-06-10
```
jrharvey@jrharvey-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 2394.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 6003.57
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 2394.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5999.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 2394.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5999.33
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 2394.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 5999.34
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

jrharvey@jrharvey-desktop:~$ 

```




This is under load

---

