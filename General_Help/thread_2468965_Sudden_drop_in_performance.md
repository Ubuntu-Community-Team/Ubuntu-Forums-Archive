---
title: "Sudden drop in performance?"
date: 2021-11-15
forum: General Help
---

### Post by woses21 on 2021-11-15
Hello,
I have been troubleshooting some strange issues that accompany a large drop in performance of my machine. The desktop is only a few months old and ran beautifully for a few months. A few weeks ago I rearranged my office and the computer has not been the same since. First it was display issues where only the display port worked and settings were unchangeable. A fresh Ubuntu install resolved that problem, but now the machine performance is in the toilet. Most steam games are choppy and unplayable and my 8 core cpu is taxed up to 60 - 80% running the average video game. Is there anything that can cause a drop in performance like this, or any suggestions for further troubleshooting?

---

### Post by TheFu on 2021-11-15
Check the system logs for any hardware issues. Always start there.  Look for warnings and errors.  Take the exact text for the error and plug that into a search engine - often it will answer the question of what is wrong and how to fix it.

When a GPU is performance badly, check that the correct drivers are loaded.  For AMD and Intel GPUs, that should happen automatically since the drivers are included with the kernel. Depending on the GPU and Ubuntu release installed, it may be necessary to use a newer kernel.

For nvidia, run 
**sudo ubuntu-drivers autoinstall**
That should get the correct, latest, supported driver for the GPU.

But start by checking the system logs.  Always, always, always, start there.

---

### Post by Doug S on 2021-11-16
I agree with TheFu, check system logs first.

There is [a recent script]("https://github.com/UbuntuForums/system-info") that will give us some needed information about your system. Please run it, saving the report to the place where it asks, and give us the link here (or just post the whole report herein, as an attachment).

Also, what CPU frequency scaling driver and governor are you using? For example:

```
doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver:intel_pstate
/sys/devices/system/cpu/cpu10/cpufreq/scaling_driver:intel_pstate
...
/sys/devices/system/cpu/cpu9/cpufreq/scaling_driver:intel_pstate
doug@s19:~/temp-k-git/linux$ [COLOR="#FF0000"]grep . /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:powersave
/sys/devices/system/cpu/cpu10/cpufreq/scaling_governor:powersave
...
/sys/devices/system/cpu/cpu9/cpufreq/scaling_governor:powersave
```

---

### Post by dragonfly41 on 2021-11-16
I would also follow the clues. What might have physically changed in a physical relocation in the office relocation?
Correct USB ports (2 or 3) reconfigured?
Has memory been dislodged?
etc.
A useful GUI for monitoring performance is Stacer.

---

