---
title: "powernowd and Dapper"
date: 2007-10-17
forum: General Help
---

### Post by sonicbuddha on 2007-10-17
I'm a recent convert from Fedora to Dapper LTS (tired of chasing upgrades!) on my servers.  My question is one of clarification.  I've installed powernowd, the Debian/Ubuntu alternative to cpuspeed in Redhat/Fedora, and it seems to install fine.  powernow_k8 gets loaded into the kernel, dmesg shows that the cpu is recognized and stepping enabled, the sys filesystem shows that its set my processor to its lowest setting (/sys/devices/system/cpu/cpu0/cpufreq/scaling_setspeed), but /proc/cpuinfo still shows the processor running at full speed.  This only occurs on the i686 or Server kernels, which are SMP enabled.  The UP i386 kernel accurately shows the processor stepped in /proc/cpuinfo.  

Enabling power management is pretty essential for me on my home server so I need to know accurately if this is working, which it doesn't seem to be.  Can anyone give me some tips?  And, if there is a solution, what is it?

Kernels: 2.6.15-29 386/686/Server

---

### Post by DagMan on 2007-10-18
I've found that it's sort of a trial and error thing as far as getting this to work and what works with which processor.
Right now I think I actually have everything disabled and just have kernel modules handling it without any specific daemon itself running.
There is cpufrequtils, cpufreqd or something along those lines as far as helper scripts running as daemons.  Synaptic will turn up more than that probably.  
Additionaly you may want to try to look into which module handles this for your particular processor and load those modules.

In my case, and i have an intel processor so it's likely differant.  During boot I modprobe  acpi-cpufreq which loads a bunch of modules... or perhaps they're already loaded, anyhow it allows me to set the policy, ondemand, performace, conservative, and a couple of others,
to set it I have to do this as the root user, not just sudo but if your doing it at th command line and this works even without a root account enabled I think.
```
sudo su root -c "echo ondemand > /sys/devices/system/cpu/*/cpufreq/scaling_governor"
```
And that gives me ondemand.  

It helps to use the panel applet to look at your cpu scaling, it will show speed and what policy you're using if you are doing it by policies.  But if you boot up into the gui and the applet says that scaling is unsupported then it won't start to update the changes until you've gotten something working and kill the gnome-panel to reload the applet.

Make sure that things are still the same after a reboot.  when making changes sometimes not everything works out the same after a reboot, also I've loaded the wrong module when playing with this and for example in one case had it working but like 150 Mhz at the low end of a 1.6 Ghz processor so things just like to freeze pretty quickly when that happens.


It's worth a search of the forum and a google to see what your options are for your processor but on that I've had people be dead wrong about my system when their way works fine on theirs.

But yeah, the second speed thing when looking at /proc/cpuinfo is showing the current speed.  The first one is just info about the processor where it mentions speed.

---

