---
title: "underclock cpu lubuntu"
date: 2014-06-08
forum: General Help
---

### Post by mike188 on 2014-06-08
I want to set frequency limit for amd cpu on a laptop. I installed 'indicator cpufreq' and theres only one governor 'ondemand', no menu to choose from such as in ubuntu. 'Cpufrequtils' doesnt work either, for example I type 
```
sudo cpufreq-set -u 800Mhz
``` 
and after that frequency at times is at its max value. In bios theres no cpu multiplier option. How can I make those programs work and what are other solutions?

---

### Post by 3rdalbum on 2014-06-08
CPU multipliers are locked by the CPU, usually. To underclock you need to lower the bus speed in the BIOS.

Bus speed x Multiplier = CPU Clock

---

### Post by tgalati4 on 2014-06-09
Post the output of:

```
cat /proc/cpuinfo
```

The range of settings depends on the processor.

On mine:

tgalati4@tpad-Gloria7 ~ $ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 2.13GHz

I have available the following speeds:  800, 1.07, 1.33, 1.6, 1.87, 2.13 and the following governors:  ondemand, conservative, powersave, performance.

The states available for your processor may be found in /proc/acpi:


tgalati4@tpad-Gloria7 /proc/acpi/processor/CPU $ cat info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes
tgalati4@tpad-Gloria7 /proc/acpi/processor/CPU $ cat throttling
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

---

