---
title: "Need help - CPU Freq Governor (null) - Coppermine CPU"
date: 2015-04-26
forum: General Help
---

### Post by Heamogoblin on 2015-04-26
Hi there guys

I'm having a slight issue, I've just installed Lubuntu ona  Dell Inpirion 4000 laptop. Install went pretty well, apart from I dont seem able to throttle the cpu and i dont know how to install the right module for a Pentium III. 

If anyone could help me out, I'd really appreciate it

---

### Post by BazBear on 2015-04-26
I'm not being a smart butt here, but I am curious why you'd want to throttle that processor?

---

### Post by Doug S on 2015-04-26
are you saying that for this command:```
doug@doug-64:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
```you are getting this response:```
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver: No such file or directory
```Instead of something like this (maybe acpi-cpufreq instead):```
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
```If yes, then your either CPU does not have frequency scaling ability, or it is not enabled in the BIOS.

---

### Post by Heamogoblin on 2015-04-26
I'm not trying to throttle it, i'm trying to tell Lubuntu to to stop running it at 500mhz. I've since sorted it by setting it up in the BIOS to run at 700mhz when on AC and then us battery saving when on battery.

I suppose now i've done that, i really dont need to bother with this. But it still means that when the laptop is running off battery, it will be restricted to 500mhz. Would be nice if i could set it to "On Demand"

Doug - You are right on the money! Thats EXACTLY what I am getting. BTW the BIOS does have CPU scaling, which is how I was able to set the CPU to full speed (performance). 

I realise a Pentium 3 is a little old in the tooth, but I thought it would be fun to see if i could make a useable system with limited resources. I've been using Linux for the past 5 years, wouldnt say I&#8217;m genius around the Terminal, but I get by after years of using DOS.

Cheers guys!

---

### Post by Heamogoblin on 2015-04-27
Still haven't been able to solve this problem. So if anyone can help, I'd seriously appreciate it :-)

---

