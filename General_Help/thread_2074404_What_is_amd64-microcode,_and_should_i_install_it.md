---
title: "What is amd64-microcode, and should i install it"
date: 2012-10-21
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-21
using xubuntu 12.10 kernel 3.6.2
i was looking at available packages and i saw this
i have noticed when i use the ondemand governor my cores will jump to 100% during idle (under 5% cpu usage, nothing but sensor applets running)
would that package fix that on my 3.4Ghz phenom II X4

EDIT seems this did happen in 10.04, what i have monitoring my core speeds just seems to detect the single millisecond my core jumps up

---

### Post by Lisiano on 2012-10-21
In my understanding, the only use of microcode for us is for attempting to OC the CPU. So this will probably not help you. There was a way to decrease the "sensitivity" of a governor. I'll look into it in a minute.

EDIT: Found a good wiki page for controlling how governors work. [https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling](https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling)

---

### Post by pqwoerituytrueiwoq on 2012-10-21
that would be for software over-clocking right, or would that help when over-clocking from the BIOS?
i have plenty of OC headroom with max temps of 44C and i intend to use it one day

---

### Post by pqwoerituytrueiwoq on 2012-10-21
> To change when the ondemand governor switches to a higher multiplier, one can manipulate /sys/devices/system/cpu/cpufreq/ondemand/up_threshold. Determine the current setting by issuing the following command as root: 
```
 # cat /sys/devices/system/cpu/cpufreq/ondemand/up_threshold  The value 
```returned should be 95, the default setting as of kernel version 3.0. This means that the ondemand governor currently increases the clock rate if a core reaches 95% utilization.
then why it is going from 800Mhz to 3.4Ghz on 2 to 4 cores at under a 5% idle cpu usage

i am on my laptop right now so i am using it as a example it has 2 speeds 1 and 2 Ghz
it it takes a 95% usage to bump up why is it at 2 Ghz?

---

### Post by Lisiano on 2012-10-24
I don't know exactly. You could try increasing the sampling rate (Increase the delay between samples).

It might be possible that the CPU usage percentage is shown relative to the scaling_max, or the speed set on Userspace. This are just my thoughts, maybe I'm wrong.

---

