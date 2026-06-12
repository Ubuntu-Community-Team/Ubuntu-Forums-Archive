---
title: "LUBUNTU Where is configuration cpu power profiles ?"
date: 2020-07-30
forum: General Help
---

### Post by aug7744 on 2020-07-30
Using Lubuntu 20.04. Where is configuration to change cpu power profiles (energy saver and high performance) ? Thanks for reply.

---

### Post by CelticWarrior on 2020-07-30
Nvidia or AMD?

---

### Post by Doug S on 2020-07-30
It depends on which CPU frequency scaling driver you are using. Do, and for example:

```
$ grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu1/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu2/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu3/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu4/cpufreq/scaling_driver:intel_cpufreq
/sys/devices/system/cpu/cpu5/cpufreq/scaling_driver:intel_cpufreq
```

But anyhow, for just changing governors, this is somewhat universal:

```
doug@s18:~/idle$ grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor:performance
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor:performance
doug@s18:~/idle$ echo ondemand | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
ondemand
doug@s18:~/idle$ grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor:ondemand
/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor:ondemand
```

And the available list:

```
$ grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_governors
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu4/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu5/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
```

---

### Post by aug7744 on 2020-07-31
Not have an tool with GUI to change power profiles ?

---

### Post by Doug S on 2020-07-31
> **aug7744 said:**
> Not have an tool with GUI to change power profiles ?Yes there is, I think. I have absolutely no use for such things.

---

### Post by aug7744 on 2020-08-02
@Doug S

"It depends on which CPU frequency scaling driver you are using. Do, and for example:
$ grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_cpufreq"

CPU is AMD. I can change to /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:amd_cpufreq ?

$ grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_governors
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu4/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil
/sys/devices/system/cpu/cpu5/cpufreq/scaling_available_governors:conservative ondemand userspace powersave performance schedutil

How to select cpu power profile power saver and make selected how default allways when starting the system ?

---

### Post by Doug S on 2020-08-02
> **aug7744 said:**
> CPU is AMD. I can change to /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:amd_cpufreq ?

How to select cpu power profile power saver and make selected how default allways when starting the system ?

There is no such driver as amd_cpufreq, that I am aware of.
You are probably using the acpi-cpufreq CPU frequency scaling driver and the ondemand governor by default.
I already showed you how to change the governor.
I would not recommend changing to the powersave governor for the default, as that will lock your CPU frequencies at their lowest possible value. the ondemand governor provides a good tradeoff between powersaving and responsiveness.

---

### Post by aug7744 on 2020-08-03
You known any utility tool that display CPU frequency in systray ?

---

### Post by aug7744 on 2020-08-07
Linux is creating some problems for me.
First crash using Lubuntu at point that the only option was power off the computer when starting an software in full screen.
One system that for change cpu power modes need several commands ? If the user need run an software that need cpu power need AGAIN run all commands ! THAT IS MADNESS !
Yes Linux system is very good and fast, but hat mania of to do commands for simple tasks is annoying at point of headache.
The user need like to do commands to use it.
I in moment had changed to power mode now not is being possible return to powersave and all times that I need to run an software need to change the cpu power profile !!
I not have knowledge if only Lubuntu is that problem, but has others strange problems how example not is possible scroll an page in each time using mouse scroll instead only lines are possible and the roll bar of right side of windows if hard to select, not is possible edit or create link in start menu ,  etc.
My first experience with Linux not is being good.

Have any distro that is more windows to configure that type of component (cpu power mode) ?
I have installed (NEED TO INSTALL AN SOFTWARE TO BE MORE EASY TO CONFIGURE !) cpufreq and when restarted the system now is displayed an icon in systray with options to change the cpu power profile, but NOT WORK.
Any help is good to me to read and have an good day.

---

### Post by maglin2 on 2020-08-07
Sidestepping your specific question, I just install tlp for laptop power management and let it do its thing. You can check what it's up to in respect of cpu with sudo tlp-stat -p

More generally, the most gui menu focussed version of ubuntu I know of is kubuntu. It has menus for most things in system settings.

---

### Post by dragonfly41 on 2020-08-07
This is a new subject matter for me so I am also learning.
Start by installing Synaptic Package Manager.
When installed search "cpu" and in there is "cpufrequtils".
You can tick this and then apply to install.
I see also "gkrellm-cpufreq" which apparently is a plugin for GKrellM.
Since I have that installed I tried this plugin.
Launch GKRellM, right click, Plugins, select CPUFreq.

Here is info on this plugin.

CPU frequency plugin
gkrellm2-cpufreq 0.6.4,  [http://chw.tks6.net/rub/7](http://chw.tks6.net/rub/7)
by Christoph Winkelmann,  [email]chw@tks6.net[/email]


Enabling and disabling display of governor, frequency or slider only
takes effect after change of theme, change of width, or restart.


The maximal frequency found during this run is saved for the next run
when this page is viewed.


Any suggestions are welcome!

---

### Post by aug7744 on 2020-08-13
Thanks :)

---

