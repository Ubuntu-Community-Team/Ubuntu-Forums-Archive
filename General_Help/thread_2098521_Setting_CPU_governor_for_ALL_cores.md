---
title: "Setting CPU governor for ALL cores"
date: 2012-12-26
forum: General Help
---

### Post by jlacroix on 2012-12-26
I have three machines, and I've been experimenting with commands to set the CPU frequency scaler by hand. This command works on each of my machines, except one of them:

```

sudo cpufreq-set -r -g performance

```

On both of my Core i series machines, that sets the CPU governor to performance for each core. However, on my Intel Core 2 Quad machine, when I run that command, the first core cranks up to 2400Mhz, but the other three remain at 1600.

I know the third machine has a different processor, but I'm still surprised it would refuse to crank up the other cores. Perhaps my command needs to be adjusted?

---

### Post by rnerwein on 2012-12-27
> **jlacroix said:**
> I have three machines, and I've been experimenting with commands to set the CPU frequency scaler by hand. This command works on each of my machines, except one of them:

```

sudo cpufreq-set -r -g performance

```On both of my Core i series machines, that sets the CPU governor to performance for each core. However, on my Intel Core 2 Quad machine, when I run that command, the first core cranks up to 2400Mhz, but the other three remain at 1600.

I know the third machine has a different processor, but I'm still surprised it would refuse to crank up the other cores. Perhaps my command needs to be adjusted?
hi
on your system you will find in the path:
/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
try in a terminal:
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
to see how your governor is set ( default on ubuntu is ondemand - wich is i think is the best solution).
performance is causing a higher energy using.
i have a own monitor that shows me the frequncy for each cpu and i can see that when i am running some tests in parallel it works perfect.
why should i change it.
to be on the saver side use "sysctl"  with the config files /etc/sysctl.conf
cheers

---

### Post by sandyd on 2012-12-27
> **jlacroix said:**
> I have three machines, and I've been experimenting with commands to set the CPU frequency scaler by hand. This command works on each of my machines, except one of them:

```

sudo cpufreq-set -r -g performance

```

On both of my Core i series machines, that sets the CPU governor to performance for each core. However, on my Intel Core 2 Quad machine, when I run that command, the first core cranks up to 2400Mhz, but the other three remain at 1600.

I know the third machine has a different processor, but I'm still surprised it would refuse to crank up the other cores. Perhaps my command needs to be adjusted?

Have you checked the status of the governers on the other cores with```
cpufreq-info
```?

---

### Post by jlacroix on 2012-12-27
> **rnerwein said:**
> hi
on your system you will find in the path:
/sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
try in a terminal:
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
to see how your governor is set ( default on ubuntu is ondemand - wich is i think is the best solution).
performance is causing a higher energy using.
i have a own monitor that shows me the frequncy for each cpu and i can see that when i am running some tests in parallel it works perfect.
why should i change it.
to be on the saver side use "sysctl"  with the config files /etc/sysctl.conf
cheers
Thank you, but I'm aware of what each governor does and how it affects energy efficiency. The performance governor was just an example. Regardless of what I manually set my cores to, only the first one changes. Per the man page for cpufreq-set, I can pass the "-r" option for it to apply changes to each core. But it doesn't.

On my systems I have written bash scripts that allow me to handle power efficiency better than Ubuntu does by default, but I can't manage this if only one core is set.

> **sandyd said:**
> Have you checked the status of the governers on the other cores with```
cpufreq-info
```?
Yes, I've looked at the statuses and ran various commands, but they all just tell me what I already know, that when I tell cpufreq-set to change the governor of each core, it only sets the governor for the first one.

---

### Post by rnerwein on 2012-12-28
> **jlacroix said:**
> Thank you, but I'm aware of what each governor does and how it affects energy efficiency. The performance governor was just an example. Regardless of what I manually set my cores to, only the first one changes. Per the man page for cpufreq-set, I can pass the "-r" option for it to apply changes to each core. But it doesn't.

On my systems I have written bash scripts that allow me to handle power efficiency better than Ubuntu does by default, but I can't manage this if only one core is set.


Yes, I've looked at the statuses and ran various commands, but they all just tell me what I already know, that when I tell cpufreq-set to change the governor of each core, it only sets the governor for the first one.

hi
as you see in my post you can use /etc/sysctl.conf to set the cpufrequ in
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
.......
in /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
you find all available values.
from bash you can set it (must be root) via
e.g. echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
this for cpu0, cpu1 .....
cheers

---

### Post by jlacroix on 2012-12-29
> **rnerwein said:**
> hi
as you see in my post you can use /etc/sysctl.conf to set the cpufrequ in
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
.......
in /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
you find all available values.
from bash you can set it (must be root) via
e.g. echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
this for cpu0, cpu1 .....
cheers
Thanks, that works. But I'm curious why the "-r" flag in cpufreq-set works fine on two of my machines, but not this one. If I set the frequency with the command you posted it works but not with cpufreq-set.

Basically, I wrote a bash script that handles powersaving (and coupled with KDE's power management it runs my CPU much cooler) but it relies on cpufreq-set working...

---

### Post by rnerwein on 2012-12-30
> **jlacroix said:**
> Thanks, that works. But I'm curious why the "-r" flag in cpufreq-set works fine on two of my machines, but not this one. If I set the frequency with the command you posted it works but not with cpufreq-set.

Basically, I wrote a bash script that handles powersaving (and coupled with KDE's power management it runs my CPU much cooler) but it relies on cpufreq-set working...
hi
back to the roots. i think the only reliable tool is the shell - if you know what you do !
shell is a (good) monster tool. 
for me 98% working in a terminal (exclud firefox). ;-)
cheers

---

