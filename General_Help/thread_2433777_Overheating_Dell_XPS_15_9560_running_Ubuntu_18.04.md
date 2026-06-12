---
title: "Overheating Dell XPS 15 9560 running Ubuntu 18.04"
date: 2019-12-25
forum: General Help
---

### Post by citizensnip5 on 2019-12-25
Hey there. I've been using Ubuntu as my sole OS (no Windows) on my Dell XPS 15 9560 for a couple of years now. I use KDE Plasma, Ubuntu 18.04, kernel version 4.15.0-72-generic, BIOS version 1.12.1 (this isn't the latest BIOS version, though nothing in the notes for the later versions suggests that an upgrade would fix the issue I'm about to describe). I recently turned off auto-suspend, as I have two cron jobs that backup different parts of my system using restic every night, and these obviously won't run unless the machine is on. I leave it plugged into AC power overnight. However, when I go to my laptop in the morning, the thing's fan is spinning between 4000 and 5000 rpm and the CPU temperature has climbed to 70+ degrees C (read using the sensors command). Here's the kicker: nothing is happening on the system when this is going on, other than my screensaver (xscreensaver) running. htop reports no heavy CPU or memory load. The backup jobs were completed hours ago. The thing is idle. And, when I start using it, the fans slow down over the next couple minutes and the temperature drops to normal levels.

Things I've tried that didn't fix the problem:
[LIST]
[*]Switched from NVIDIA graphics to Intel integrated graphics. 
[*]Disabled Intel pstate (now using acpi-cpufreq). 
[*]Verified thermald is running. 
[*]Installed and started using tlp. 
[/LIST]

Here's the output of sensors right now, when it's not overheating:
```

pch_skylake-virtual-0
Adapter: Virtual device
temp1:        +43.5°C  

acpitz-virtual-0
Adapter: Virtual device
temp1:        +25.0°C  (crit = +107.0°C)

dell_smm-virtual-0
Adapter: Virtual device
Processor Fan: 2504 RPM
Video Fan:     2533 RPM
CPU:            +46.0°C  
Ambient:        +45.0°C  
Ambient:        +42.0°C  
Other:          +32.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +47.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +46.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +46.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +45.0°C  (high = +100.0°C, crit = +100.0°C)

```

Here's the output of cpufreq-info:
```

cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.40 GHz, 2.30 GHz, 2.10 GHz, 2.00 GHz, 1.90 GHz, 1.80 GHz, 1.60 GHz, 1.50 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz, 1000 MHz, 900 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.50 GHz:0.00%, 2.50 GHz:9.60%, 2.40 GHz:2.64%, 2.30 GHz:9.81%, 2.10 GHz:3.70%, 2.00 GHz:1.54%, 1.90 GHz:1.47%, 1.80 GHz:2.23%, 1.60 GHz:2.45%, 1.50 GHz:2.29%, 1.40 GHz:2.88%, 1.30 GHz:3.91%, 1.20 GHz:8.57%, 1000 MHz:14.59%, 900 MHz:20.63%, 800 MHz:13.68%  (3223444)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.40 GHz, 2.30 GHz, 2.10 GHz, 2.00 GHz, 1.90 GHz, 1.80 GHz, 1.60 GHz, 1.50 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz, 1000 MHz, 900 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.50 GHz:0.00%, 2.50 GHz:11.56%, 2.40 GHz:0.74%, 2.30 GHz:1.77%, 2.10 GHz:1.96%, 2.00 GHz:1.37%, 1.90 GHz:1.43%, 1.80 GHz:2.99%, 1.60 GHz:3.24%, 1.50 GHz:2.79%, 1.40 GHz:3.10%, 1.30 GHz:4.07%, 1.20 GHz:9.39%, 1000 MHz:15.14%, 900 MHz:20.99%, 800 MHz:19.45%  (2970693)
analyzing CPU 2:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 2
  CPUs which need to have their frequency coordinated by software: 2
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.40 GHz, 2.30 GHz, 2.10 GHz, 2.00 GHz, 1.90 GHz, 1.80 GHz, 1.60 GHz, 1.50 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz, 1000 MHz, 900 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.50 GHz:0.00%, 2.50 GHz:12.52%, 2.40 GHz:0.79%, 2.30 GHz:1.86%, 2.10 GHz:2.09%, 2.00 GHz:1.42%, 1.90 GHz:1.49%, 1.80 GHz:3.17%, 1.60 GHz:3.38%, 1.50 GHz:2.88%, 1.40 GHz:3.23%, 1.30 GHz:4.22%, 1.20 GHz:9.56%, 1000 MHz:16.13%, 900 MHz:19.95%, 800 MHz:17.30%  (2953973)
analyzing CPU 3:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 3
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.40 GHz, 2.30 GHz, 2.10 GHz, 2.00 GHz, 1.90 GHz, 1.80 GHz, 1.60 GHz, 1.50 GHz, 1.40 GHz, 1.30 GHz, 1.20 GHz, 1000 MHz, 900 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance, schedutil
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.50 GHz:0.00%, 2.50 GHz:12.53%, 2.40 GHz:0.81%, 2.30 GHz:1.93%, 2.10 GHz:2.14%, 2.00 GHz:1.48%, 1.90 GHz:1.55%, 1.80 GHz:3.21%, 1.60 GHz:3.46%, 1.50 GHz:3.00%, 1.40 GHz:3.40%, 1.30 GHz:4.39%, 1.20 GHz:9.73%, 1000 MHz:15.54%, 900 MHz:20.07%, 800 MHz:16.75%  (3019504)

```

Here's a screenshot of my Energy Saving settings. Notice that "Suspend session" is unchecked:
[ATTACH=CONFIG]284676[/ATTACH]

I've not noticed this issue until now, I guess because my computer was always suspending itself before it could happen, before I was doing these nightly backups.

Any help is greatly appreciated. Merry Christmas!

---

### Post by CelticWarrior on 2019-12-25
If it overheats only when under stress it probably means it needs cleaning.

---

### Post by GhX6GZMB on 2019-12-25
Open the machine and clean the fan.

---

### Post by citizensnip5 on 2019-12-25
> **CelticWarrior said:**
> If it overheats only when under stress it probably means it needs cleaning.

That's the thing, it is **not** under stress when this happens. It's idle.

---

### Post by citizensnip5 on 2019-12-25
> **ml9104 said:**
> Open the machine and clean the fan.

Probably worth doing, yeah. I don't think this gets to the root of the problem, though. I see lower temperatures when I'm training neural networks on this thing than when it's doing nothing in the morning, as I described in the post. Will let you know if cleaning helps.

---

### Post by CatKiller on 2019-12-25
> **citizensnip5 said:**
> I use KDE Plasma, Ubuntu 18.04, kernel version 4.15.0-72-generic

You could try installing the **linux-generic-hwe-18.04** package to see if it helps.

---

### Post by bunny9000 on 2019-12-25
If it was running the screensaver all night it wasn't doing nothing. If it's graphical rather than just a blank screen try switching to a blank screen or just setting the screen to turn off as you say it cools off when you start to use it once the screensaver it stopped. Does it idle hot if left for hours without a screensaver running and just a simple picture slideshow running or even nothing at all.

If it is the screensaver then it should warm up if left all day with the screensaver running.

It doesn't sound like a dust issue as the thing wouldn't cool down once you start to use it. More load would just expose an underlying fan blockage issue rather than it 'idling' hot and then cooling when in use.

Although it probably won't hurt to check the dust levels as even if dust is not the issue it's just good housekeeping to clean them every year or couple of years.

---

### Post by citizensnip5 on 2019-12-25
> **bunny9000 said:**
> If it was running the screensaver all night it wasn't doing nothing. If it's graphical rather than just a blank screen try switching to a blank screen or just setting the screen to turn off as you say it cools off when you start to use it once the screensaver it stopped. Does it idle hot if left for hours without a screensaver running and just a simple picture slideshow running or even nothing at all.

If it is the screensaver then it should warm up if left all day with the screensaver running.

It doesn't sound like a dust issue as the thing wouldn't cool down once you start to use it. More load would just expose an underlying fan blockage issue rather than it 'idling' hot and then cooling when in use.

Although it probably won't hurt to check the dust levels as even if dust is not the issue it's just good housekeeping to clean them every year or couple of years.

I'll change to it to blank and see how it goes. Good idea.

---

### Post by citizensnip5 on 2019-12-26
Turning the screensaver to blank seemed to help a bit, but the temperature still dropped by about 10 degrees C after I started using it this morning. And the fan is completely off, having been running at over 3000 rpm when I picked it up this morning. EDIT: Realized that I also unplugged the laptop from AC power when seeing this temperature drop and the fans turning off. Makes me wonder if having it plugged is switching to a different energy management profile that causes it to run hot overnight like this.

> **CatKiller said:**
> You could try installing the **linux-generic-hwe-18.04** package to see if it helps.

Trying this next.

---

### Post by oldfred on 2019-12-26
I would still update UEFI from Dell. 
Details do not always list all the fixes.

       Spectre virus, repoline
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

### Post by citizensnip5 on 2019-12-27
I installed the HWE kernel, but the problem persisted. Also cleaned out the fans.

What seems to have finally fixed the issue, i.e. no crazy heating and  fan action overnight, is changing CPU_HWP_ON_AC in  /etc/default/tlp from balance_performance to balance_power.

Thanks for the help everyone.

---

