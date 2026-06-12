---
title: "cpufreq-selector missing in Gutsy??"
date: 2007-10-27
forum: General Help
---

### Post by ctsdownloads on 2007-10-27
What happened to to cpufreq-selector? It was available in the Gutsy release candidate, yet I reinstall with the actual release and boom, it is not available from the install or the repos with EVERYTHING available enabled. I need a clean GUI for CPU throttling please, not interested in the command line stuff.

Plugins are installed, too along with the utilities.

thanks

---

### Post by ctsdownloads on 2007-10-27
Fixed this by reinstalling cpufreqd and cpufreq-utiltis, I also re-installed gnome-applets just for good measure, this helped. :)

---

### Post by chrisccoulson on 2007-10-27
I don't have cpufreqd installed, and I get CPU throttling via powernowd. If you want to manually adjust the CPU frequency, you can do this using the CPU Frequency Scaling Monitor applet on your GNOME panel. To allow it to adjust the frequency, run:
```
sudo dpkg-reconfigure gnome-applets
```
and select to install cpufreq-selector with suid root.

---

### Post by ctsdownloads on 2007-10-27
Cool, thanks. So what would one do who is using an intel chip instead? I say this as I believe that powernowd is AMD only?

---

### Post by chrisccoulson on 2007-10-28
I thought powernowd worked with Intel systems as well?

---

### Post by ctsdownloads on 2007-10-28
Checked into it, it does, it's the naming scheme that threw me off - Intel and AMD both work.

---

### Post by njparton on 2007-10-30
> **chrisccoulson said:**
> I don't have cpufreqd installed, and I get CPU throttling via powernowd. If you want to manually adjust the CPU frequency, you can do this using the CPU Frequency Scaling Monitor applet on your GNOME panel. To allow it to adjust the frequency, run:
```
sudo dpkg-reconfigure gnome-applets
```
and select to install cpufreq-selector with suid root.

I've done that - should it give me a new entry on one of the gnome menus somewhere or does it run in the background?

---

### Post by chrisccoulson on 2007-10-30
You need to add the frequency scaling monitor applet to your panel. Clicking on the applet will then present you with a list of options

---

### Post by njparton on 2007-10-30
> **chrisccoulson said:**
> You need to add the frequency scaling monitor applet to your panel. Clicking on the applet will then present you with a list of options

Aha, gotcha, thanks.

---

### Post by kubel on 2007-11-07
> **chrisccoulson said:**
> I don't have cpufreqd installed, and I get CPU throttling via powernowd. If you want to manually adjust the CPU frequency, you can do this using the CPU Frequency Scaling Monitor applet on your GNOME panel. To allow it to adjust the frequency, run:
```
sudo dpkg-reconfigure gnome-applets
```
and select to install cpufreq-selector with suid root.

This is exactly what I was looking for. Thanks chris!

---

### Post by bluetooth on 2007-11-10
I need help with enabling CPU frequency scaling on Gutsy. It simply doesn't work. I got message "CPU frequency scaling is unsupported" and my CPU works at 600MHz while it should be able to work up to 2GHz :( If I try sudo modprobe speedstep-centrino, I got> FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.22-14-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Device or resource busy
Will approciate any help to make my CPU frequancy scaling to work

---

### Post by Haak on 2007-11-30
same 'scaling not supported' problem here. 

I hava an E4300 and Vista scales it up and down all the time. Have tried cpufreq, powernow and some others. The governors are not installed somehow. And with all named possibilities still won't install. 

There seems to be a bug(forgot the ID).

---

### Post by A-dogg on 2007-11-30
perfect! I installed powernowd and reconfigured the gnome-applets to show the options in the monitoring applet. I guess this means I don't need to install cpufreqd and cpufrequtils, then?

---

### Post by aselvan on 2008-01-13
> **bluetooth said:**
> I need help with enabling CPU frequency scaling on Gutsy. It simply doesn't work. I got message "CPU frequency scaling is unsupported" and my CPU works at 600MHz while it should be able to work up to 2GHz :( If I try sudo modprobe speedstep-centrino, I got
Will approciate any help to make my CPU frequancy scaling to work

Not sure if you still have problems. I had the same issue and it turns out the powernowd was not installed in fresh install of 7.10. I installed it now the gnome-cpufreq-applet allows 8 frequency to select from in addition to "conservative", "ondemand", "powersave","performance". Personally, I like the "ondemand" as it works real nice for my needs and keeps my CPU running cool. 

Make sure the acpi-cpufreq modules loads. See below..

aselvan@panther:~$ lsmod |grep cpufreq
acpi_cpufreq           10568  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor              32072  2 acpi_cpufreq,thermal

---

