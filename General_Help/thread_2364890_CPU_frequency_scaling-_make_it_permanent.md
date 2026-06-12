---
title: "CPU frequency scaling- make it permanent"
date: 2017-06-29
forum: General Help
---

### Post by svennils on 2017-06-29
Hi,
I'm trying to make my cpu scaling frequencies permanent on  the different governors.
I have a samsung 400b4b laptop with intel 2.9Ghz I5 cpu, it can range from 800mhz to 2,9ghz. 
I have the tray applet to select governor, powersave and performance are available.
I would like powersave to stay at 800mhz permanently, i select this governor when on battery. 
In terminal " sudo cpufreq-set -u 800Mhz" works, but frequently gets overridden by various apps and programs, as "cpufreq-info" will tell me. 
Sometimes i have to set it several times before it stays, for an unspecified amount of time. 

I've installed sysfs and edited sysfs.conf to include as per [https://wiki.debian.org/HowTo/CpuFrequencyScaling:](https://wiki.debian.org/HowTo/CpuFrequencyScaling:)

"mode devices/system/cpu/cpufreq/powersave = 644
devices/system/cpu/cpufreq/powersave/scaling_max_freq = 800000
devices/system/cpu/cpufreq/powersave/scaling_min_freq = 800000
devices/system/cpu/cpufreq/powersave/freq_step = 10
devices/system/cpu/cpufreq/powersave/up_threshold = 45
devices/system/cpu/cpufreq/powersave/ignore_nice_load = 1
devices/system/cpu/cpufreq/powersave/sampling_down_factor = 10"

To no effect. 

How can i set the max and min frequencies for each governor (performance and powersave) and make them permanent across reboots?

---

### Post by pqwoerituytrueiwoq on 2017-06-29
most applets have not been updated for intel_powerstate

The old gonvern is not used for modern intel chips it now uses intel_powerstate, it only has performance and power-save modes
and powersave does not do much if anything 4cores running in the turbo range at idle

i made a script to set it on xubuntu that works via the xfce4-genmon-plugin
[https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin](https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin)
if you run this command you can change the governor
cpu-freq-plugin $CORE_NUMBER --set

data can be found here in the system
/sys/devices/system/cpu/cpu$CORE_NUMBER/cpufreq

you would need to save the current governor on shutdown and reapply it at boot to do it, but the difference is so minimal it is not worth bothering with imo

---

### Post by CatKiller on 2017-06-29
> **svennils said:**
> I would like powersave to stay at 800mhz permanently, i select this governor when on battery.

You probably don't want to do that. Intel's powersaving philosophy has been Race-to-Sleep: get whatever task needs to be done over with as quickly as possible so that the processor can spend more time in very-low-power modes. If you fix the clock speed low, the processor and all the auxiliary support stuff is powered on for longer, which drains more power.

If you want to preserve battery power, you'll probably have more success using powertop to see which processes are waking the processor out of its power-sipping slumber.

As pqwoerituytrueiwoq says, Intel processors use pstates to control the frequency scaling. If you want to change that, you'll either need to use a tool that can manipulate pstates or turn off pstate support and use the older manual cpufreq methods.

---

