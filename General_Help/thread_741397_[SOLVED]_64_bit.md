---
title: "[SOLVED] 64 bit?"
date: 2008-03-31
forum: General Help
---

### Post by Raccoon1400 on 2008-03-31
Is this a 64 bit processor?
Probably be a stupid question, but this is the best way to learn.
Is this enough info? If not, where do I look to find it?

duncan@duncan-laptop:~$ cat/proc/cpuinfo
bash: cat/proc/cpuinfo: No such file or directory
duncan@duncan-laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
stepping        : 6
cpu MHz         : 800.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3195.62
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
stepping        : 6
cpu MHz         : 800.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3192.05
clflush size    : 64

duncan@duncan-laptop:~$

---

### Post by pytheas22 on 2008-03-31
All Core 2s should be 64-bit, or so wikipedia says: [http://en.wikipedia.org/wiki/Intel_Core_2](http://en.wikipedia.org/wiki/Intel_Core_2) .  And you have a Core 2.

---

### Post by Raccoon1400 on 2008-03-31
I finally leaned the difference between 32 and 64 bit, and if this is a 64 bit processor, I will upgrade to the 64 bit OS when Hardy comes out.

I was wondering, is this one processor with two 1.6GHz cores, or two processors each with two 800MHz cores? The info suggests the latter.

---

### Post by Rocket2DMn on 2008-03-31
You can check for sure using
```
sudo lshw -C cpu | grep width
```
The "width" tells you what bit processor you have.

A Core 2 is one processor die with 2 cores on the chip.

---

### Post by pytheas22 on 2008-03-31
Yes, it looks like two processors @ 800mhz each.  But I don't really know how to interpret this information for sure.

---

### Post by Rocket2DMn on 2008-03-31
The 800mhz is because the processors are scaling down when they aren't getting heavy usage, this is a power saving feature, and helps to reduce heat.

---

### Post by Raccoon1400 on 2008-03-31
Am I entering this wrong?

```
duncan@duncan-laptop:~$ sudo lshw -C | grep width
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

duncan@duncan-laptop:~$ \      
```

---

### Post by Rocket2DMn on 2008-03-31
Yes, you forgot the "cpu" part
```
sudo lshw -C cpu | grep width
```
it's the same as
```
sudo lshw -class cpu | grep width
```
You can take out the grep part to see more info
```
sudo lshw -C cpu
```
Or to see all kinds of info about your computer, just do
```
sudo lshw
```

---

### Post by tribaal on 2008-03-31
Your processor has the "lm" instruction set, so it is 64bits capable.
:)

- Trib'

---

### Post by Raccoon1400 on 2008-03-31
Thanks. I will upgrade to 64 bit when Hardy comes out.

tribaal, I love your signature. It's funny because it's true.

---

### Post by tribaal on 2008-03-31
Hehe thanks :)

I suggest you install a 64bits Gutsy now, so that you can use the update manager to upgrade to hardy 64.
It's not possible to upgrade from a 32bits OS to a 64bits OS: You have to reinstall the system (make sure you backup your files though :) ).

Just my 2 centimes.

- Trib'

---

