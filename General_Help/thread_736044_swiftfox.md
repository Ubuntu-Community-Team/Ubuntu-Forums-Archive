---
title: "swiftfox"
date: 2008-03-26
forum: General Help
---

### Post by go_beep_yourself on 2008-03-26
Which Swiftfox deb is appropriate for this cpu.

```
root@ubuntu-desktop:~# cat /proc/cpuinfo 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : Unknown CPU Type
stepping        : 1
cpu MHz         : 1493.726
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
bogomips        : 2988.97
clflush size    : 32

root@ubuntu-desktop:~# hwinfo --cpu
01: None 00.0: 10103 CPU                                        
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 6.8.1 "Unknown CPU Type"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,mmx,fxsr,sse,syscall,mmxext,3dnowext,3dnow,up,ts
  Clock: 1493 MHz
  BogoMips: 2988.97
  Cache: 256 kb
  Config Status: cfg=new, avail=yes, need=no, active=unknown
root@ubuntu-desktop:~# 
```


Why this one and not another one. None seem to match exactly.

[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)

Select your processor

    * Athlon 64                          not 64 bit cpu
    * Athlon 64 (32bit OS)           not this
    * Athlon-XP                          my cpu doesnt say xp anywhere
    * Sempron                          dont see this anywhere
    * Duron                               or this
    * Athlon (Thunderbird)          or this
    * Pentium 4
    * Prescott
    * Core Solo/Duo
    * Pentium M
    * Pentium 3
    * Pentium 3M
    * Celeron (Willamette, Northwood, Celeron D)
    * Celeron M
    * Celeron (Coppermine, Tualatin)
    * Pentium 2

Is there any benchmarks done to see what is faster?

latest firefox 3 beta
swiftfox
swiftweasle

---

### Post by Gavin77 on 2008-03-26
Not sure about the 3 beta version but if you want to use the latest stable version then on this page - [http://getswiftfox.com/br18.htm](http://getswiftfox.com/br18.htm) you can install "Swiftfox 2.0.0.13pre-2 for AMD".

---

### Post by go_beep_yourself on 2008-03-26
How come that name does not same anything about amd. It doesn't appear to be optimized for the particular processor.

---

### Post by p_quarles on 2008-03-26
Can you post the output of the following two commands?
```
sudo lshw | grep -A 5 cpu
```
and
```
uname -a
```
"lshw" may not be installed already, but it is available in the repositories.

---

