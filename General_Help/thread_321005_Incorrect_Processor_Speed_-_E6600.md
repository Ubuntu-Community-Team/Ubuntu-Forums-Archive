---
title: "Incorrect Processor Speed - E6600"
date: 2006-12-18
forum: General Help
---

### Post by XScorpion2 on 2006-12-18
Ok, this problem has been bugging me for a few months now. Let me give you a bit of background on my PC first:
ABit AB9 (non pro) running the latest bios 1.5
Intel Core 2 Duo E6600
IDE CD-ROM (Samsung I think)
3 SATA Hard Drives

Basically after updating my bios to the latest I can get Edgy installed and running just fine. The problem that has bothered me for a few months now is that my processor is a 2.4Ghz Dual core. However, each core is only being seen as 900Mhz max, scaled down to 600Mhz. 

Now this problem I have had since day one, using kernel 2.6.16.8 I think was the first I tried all the way up to the most recent 2.6.19.1 I have also used several different distros and 32 bit as well as 64 bit versions to see if it was just that. OpenSUSE, KNOPPIX, Gentoo, Sabayon Linux, Ubuntu. Same thing in every one of them: 900Mhz max scaled down to 600Mhz.

I have turned off every type of power management option in the bios including EIST and I have also tried booting with noacpi, nofreqscaling. Finally I have also compiled my own kernel manually choosing CFLAGs as well as disabiling ACPI control in the bios directly. 

I just can't figure it out. Anyone have any suggestions or ideas?

[FONT="Courier New"]# catt /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 900.000
cache size      : 4096 KB
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
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4805.39

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 900.000
cache size      : 4096 KB
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
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4800.36[/FONT]

---

### Post by werdz on 2007-02-04
I'm using Edgy (i386 version) and having the exact same problem. It sure as hell doesn't *feel* like 600/900MHz though. XGL/beryl and various other heavy programs that'd struggle on a slow system are flying along. Also I'd have thought that running a 2.4GHz CPU that slowly would cause errors left right and centre... so it's gotta be just a reporting error...

Even weirder is that it says core 0 is at 600MHz, but core 1 is at 900MHz - is that even possible?

```

andrew@fred:~$ uname -a
Linux fred 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
andrew@fred:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 600.000
cache size      : 4096 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4902.26

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 900.000
cache size      : 4096 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 4896.92

andrew@fred:~$ 

```

I notice that we both have Abit mainboards - I have the Abit AW9D (Intel 975X chipset), could this be anything to do with it?

CPU-Z on Windows reports the correct frequency (its always either 1.6GHz or 2.4GHz depending on load).

---

