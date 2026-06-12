---
title: "Fan does not stop, powernowd daemon error"
date: 2007-10-20
forum: General Help
---

### Post by deformation on 2007-10-20
yesterday i went through hell to figure out why after upgrading my xubuntu to gutsy the fan started running crazy with no stop, even if cpu is less than 5% and the computer is idle.


it seems that the powernowd process is not starting when ubuntu starts..

this is what i get in the terminal :


> deformation@deformation-laptop:~$ sudo powernowd

powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check


anyone can relate this to the fan issue?


please help

---

### Post by deformation on 2007-10-20
bump guys any help?

---

