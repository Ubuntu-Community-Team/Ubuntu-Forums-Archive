---
title: "cpufreq in Ubuntu 16.04"
date: 2016-07-11
forum: General Help
---

### Post by denis.positron on 2016-07-11
Hi guys,

I like using cpufreq to adjust the frequency of processor cores. When I am performing basic tasks I use the minimum frequency available and, under such circumstance, the fan speed is null most of the time. When I am going to run some numerical simulations I adjust the frequency to some value near the maximum. At least it used to work until Ubuntu 14.04. Last week I installed 16.04 and since then I am in trouble with cpufreq. I've been searching in the web for a solution, until now without success. I installed indicator-cpufreq, cpufreqd, cpufrequtils, lm-sensors and psensor. The last instructions I followed were those found in the links below 

[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)
[https://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html](https://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html)
[http://ubuntuforums.org/showthread.php?t=1697022&highlight=cpufreq+16.04](http://ubuntuforums.org/showthread.php?t=1697022&highlight=cpufreq+16.04)
[http://ubuntuforums.org/showthread.php?t=1048608&highlight=cpufreq+16.04](http://ubuntuforums.org/showthread.php?t=1048608&highlight=cpufreq+16.04)

However the frequency was changing automatically after some time of reboot. When I tried to change the frequency sometimes I was successful, but the frequency changed "by itself" after some time. Because I tested lots of suggestions I found in the web, I decided to completely remove the programs listed above, undid the changes in /ect (at least the ones I remembered) and reinstalled them, however the same basic problem persists.

Somewhere in web I learned to change the frequency by typing the following in terminal

sudo sh -c "echo 800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq"
sudo sh -c "echo 800000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq"
sudo sh -c "echo 800000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq"
sudo sh -c "echo 800000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq"
sudo sh -c "echo 800000 > /sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq"
sudo sh -c "echo 800000 > /sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq"
sudo sh -c "echo 800000 > /sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq"
sudo sh -c "echo 800000 > /sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq"

(The value 800000 corresponds to the minimum frequency of my processor). However, few instants later the governor automatically changes. If I rerun the above commands, then the frequency goes again to 0.80GHz. But when I change to my Standard Account Type the frequency is at maximum and I can not change its value. Right now my processor is working in turbo mode: 2901000Hz.

In Ubuntu 14.04 cpufreq worked perfectly: I had defined the minimum frequency as default at the initialization of the system and I could change the frequency easily by just clicking in a value of frequency listed by cpufreq. I would be glad if somebody could help me to achieve the same behavior of cpufreq that I found in Ubuntu 14.04.

Best regards,

Denis

PS.: I verify the frequency of my processor with the command

cat /sys/devices/system/cpu/*/cpufreq/scaling_cur_freq

---

### Post by leozinho29_eu on 2016-07-19
Hi

I managed to change the default configuration from "ondemand" to "conservative" at every boot. To do this, I had to install some packages and edit some system files. All the steps require superuser permissions to make the changes system-wide. Be careful when making the needed editions.

The packages I had to install to make this configuration were:

```
cpufrequtils
```

and

```
sysv-rc-conf
```

I did the following: 

1) Editing the file /etc/init.d/cpufrequtils:

If using gedit, pluma, leafpad or another graphical program, remember to use gksu instead of sudo. Example:

```
gksu gedit /etc/init.d/cpufrequtils
```

I changed the line:

```
GOVERNOR="ondemand"
```

to 

```
GOVERNOR="conservative"
```

Be careful when changing the governor, I had no courage to write something not valid and see what happens. That file has helpful comments too.

2) Using sysv-rc-conf: 

```
sudo sysv-rc-conf
```

(Possibly) there will be many options (apache, bluetooth, cron, ...). One of them is ondemand and it will be started in many boot stages. Deactivate ondemand in all of them, then the configuration set at /etc/init.d/cpufrequtils will be used. Be careful to not deactivate different things.

I have seen only twice the system overriding the configuration I've done after the boot, both before the changes. Likely the ondemand script was executed, what made the governor reconfigure to ondemand.

This steps worked using Lubuntu 16.04. I believe Ubuntu uses the same configurations.

---

### Post by denis.positron on 2016-07-22
Dear leozinho29_eu,

Thank you for the detailed assistance. To unmark ondemand in sysv-rc-conf was the crucial point that I did not had tried. Thank you again. cpufreq is working like a charm.

Best regards,

Denis

---

