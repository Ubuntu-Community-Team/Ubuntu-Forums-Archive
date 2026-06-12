---
title: "Functioning fan speed control for Dell E6410 with i5 Processor?"
date: 2014-07-01
forum: General Help
---

### Post by vickoxy on 2014-07-01
Hi,
i am wondering if there is any functional fan speed control solution for Dell E6410 Laptops with Intel i5 Processors? I tried to install fancontrol and to run pwmconfig, but i get:
```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

I tried also i8kmon (which was workin on my old dell D630) but i had some erratic fan pulsing behavior. 

So i have no idea where to start now. The laptop is not hot and fan is working well, but i would like to have it started little bit later and on higher cpu temperatures...

Anyone here has Dell Latitude E6410?

Thanks!:popcorn:

---

### Post by vickoxy on 2014-07-02
I found some help here:
[https://bugs.launchpad.net/i8kutils/+bug/410596](https://bugs.launchpad.net/i8kutils/+bug/410596) (see #5) - but needed to install g++ and gcc-4.6-multilib (see #13)

But there is one problem. As soon as i execute 
> sudo ./smm 30a3
BIOS is not controlling fan speed anymore, but my sensors are not updating CPU Temp any more. 
E.g.:
> linux@linux:~$ sensors
i8k-virtual-0
Adapter: Virtual device
Right Fan:   131190 RPM
CPU:          +43.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +42.0°C  (high = +95.0°C, crit = +105.0°C)

Core 0 ande Core 2 Temp. are updated, but CPU remains on the scale noted in the moment i activated **sudo ./smm 30a3**

My **i8mon.conf** has:
> set config(0) {{-1 0} -1 60 -1 65}
set config(1) {{-1 1} 55 70 58 75}
set config(2) {{-1 2} 60 80 65 85}

That means that the fan is always off, because it does not get CPU temp. accurate.

Any idea?

---

### Post by vickoxy on 2014-07-06
no one?

---

### Post by TDully on 2014-07-15
Seems no one has any idea yet...

Have toshiba, 1080, Intel i5-4200u, Ubuntu 14.04.....MY fan is NOT coming on at all.

tried that dell trick...no luck, you try "thinkfan" but it really did nothing for me
hope we can see someting soon...

---

