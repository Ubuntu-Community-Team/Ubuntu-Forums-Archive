---
title: "Sensors help"
date: 2018-08-30
forum: General Help
---

### Post by raleigh3 on 2018-08-30
I need some help getting sensors working for my laptop.

I ran sensors-detect.

Not showing a fan speed unless my laptop doesn't have one?

```
andy@7:~$ sensors -f
acpitz-virtual-0
Adapter: Virtual device
temp1:       +125.6Â°F  (crit = +248.0Â°F)
temp2:       +125.6Â°F  (crit = +248.0Â°F)
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +66.2Â°F  (high = +221.0Â°F, crit = +221.0Â°F)
Core 1:       +78.8Â°F  (high = +221.0Â°F, crit = +221.0Â°F

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Model name:            Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
Stepping:              10
CPU MHz:               1889.935
CPU max MHz:           2000.0000
CPU min MHz:           1200.0000
BogoMIPS:              3989.94
L1d cache:             32K
L1i cache:             32K
L2 cache:              1024K
NUMA node0 CPU(s):     0,1



```

---

### Post by $yl9pAR%t on 2018-08-30
When it comes to a fan speed and/or cpu, gpu and mobo temperatures I suggest trying:
```
inxi -s
```

---

### Post by raleigh3 on 2018-08-30
Thanks. The following renders any further questions moot. :-)

I have a desktop system and an HP laptop. 

I was working on getting sensors working on it to monitor cpu and fan info. 

It wasn't showing any fan speeds. 

I have dissassembled laptops b4. 

So I decided to clean the fan. 

I noticed that many screws were different lengths and widths. 

While disconnecting some ribbon connections which were hard to see, one started falling apart. 

I decided to just salvage what I can from it. 

What do you recommend I save ? :-)

---

