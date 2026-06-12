---
title: "Easiest way to bump max CPU frequency?"
date: 2014-02-06
forum: General Help
---

### Post by yoshimitsuspeed2 on 2014-02-06
I am trying to overclock my CPU when I remember that frikken Linux limits CPU speed to a preset number based on your processor. 
I remember years ago I used cpufreq to up that but then I remember it no longer scaled, just ran at 100% all the time. 
I did some searching and found a dozen different suggestions that all  seemed way overly convoluted. In the process I found  /sys/devices/system/cpu/cpu0/cpufreq/ cpuinfo_max_freq which seems like  it should be a simple elegant solution to upping the max limit but I  cannot edit it. I tried sudo and su - with no luck. 
I want scaling, I want it to work just like it does now. I don't want  extra software or modability. I just want to up the max limit.

---

### Post by tgalati4 on 2014-02-06
Does your BIOS allow you to overclock?  Normally you would either increase the Front Side Bus (FSB) speed or the CPU multiplier (10x, 12x, 14x, etc) and then the processor would operate at a higher overall speed.  Linux will then detect the new maximum speed and set the CPU steps accordingly.  Some Intel CPU's are locked, some motherboards don't support overclocking, some BIOS's don't have the switches so you have to resort to jumpers on the motherboard.  

What is the hardware?

---

### Post by pqwoerituytrueiwoq on 2014-02-06
overclocking will usually require additional voltage (for any worthwhile OC)
BIOS overclocking will be more stable than any software overclock
if you want to try what you tried to do, do this:
[FONT=courier new]sudo chmod 644 /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_max_freq[/FONT]
if you want to edit that file try [FONT=courier new]echo 4000000 | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_max_freq[/FONT]
BTW 400000 is 4GHz

OCing via bios is the most recommended way to oc the cpu

overclock and keeping CPU scaling can be difficult, i can get +300MHz without loosing CPU scaling anything more and i loose that, but on my moms system i cant even get +100MHz without that, this is due to the different motherboard

---

