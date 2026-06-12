---
title: "Acer 5002wlmi has a very loud fan"
date: 2008-02-19
forum: General Help
---

### Post by komputes on 2008-02-19
Hi everyone,

I have a Acer Aspire 5002wlmi with a very very loud CPU fan, and it comes in whenever the CPU temperature reaches 45-47 degrees Celsius. I was wondering if someone can help me with two scripts, one that will set the CPU to 50% (800Mhz) and turn off the fan and another script to put it back to normal (1600Mhz). I was reading up on lmsensors, but it seems that the configuration really depends on the specifics of your computer. My computer does not have multiple streps, but it does have hyperthreading (still not sure what that really means) but it jumps between 800 and 1600 Mhz.

I ran sensors on my laptop and got:

```

komputes@ubuntu:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +47°C

```

I also posted the contents of my /etc/sensors.conf on this [pastebin]("http://pastebin.ca/909835")

Thanks in advance for everyone's help!

---

### Post by komputes on 2008-02-20
Also, here is my cpuinfo:

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 36
model name	: AMD Turion(tm) 64 Mobile Technology ML-30
stepping	: 2
cpu MHz		: 800.000
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips	: 1600.94
clflush size	: 64

```

---

### Post by UK-Wobbie on 2008-02-20
> **komputes said:**
> Hi everyone,

I have a Acer Aspire 5002wlmi with a very very loud CPU fan, and it comes in whenever the CPU temperature reaches 45-47 degrees Celsius. I was wondering if someone can help me with two scripts, one that will set the CPU to 50% (800Mhz) and turn off the fan and another script to put it back to normal (1600Mhz). I was reading up on lmsensors, but it seems that the configuration really depends on the specifics of your computer. My computer does not have multiple streps, but it does have hyperthreading (still not sure what that really means) but it jumps between 800 and 1600 Mhz.

I ran sensors on my laptop and got:

```

komputes@ubuntu:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +47°C

```

I also posted the contents of my /etc/sensors.conf on this [pastebin]("http://pastebin.ca/909835")

Thanks in advance for everyone's help!

I see why it's getting to hot lol The CPU is over working and the CPU fan is not doing anything.
There is a tool what i have seen, But never used it. And the tool will yet you play about with the CPU, Like over clocking.
And it will yet you play about with the fan power input and output. 

I do not know where i seen that sorry, I was busy at the time.

There is one tool what will display the CPU information in the Xfce panel.
Here [http://packages.ubuntu.com/feisty/x11/xfce4-cpu-freq-plugin](http://packages.ubuntu.com/feisty/x11/xfce4-cpu-freq-plugin)

---

### Post by komputes on 2008-02-21
Display is nice, but a GUI way of controlling the chip speed and the fan would be awesome, if you find this, please let me know ASAP. I have a few colleagues that will thank you for it.

---

### Post by komputes on 2008-02-21
I was told to use cpufrequtils by MasterShrek on #ubuntu

```
komputes@ubuntu:~$ cpufreq-info 
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.60 GHz
  available frequency steps: 1.60 GHz, 800 MHz
  available cpufreq governors: powersave, userspace, conservative, ondemand, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.

```

I was then reading the manual for cpufreq-set and read that you can set it manually, or you could use on of the governors (fancy talk for preset). Since I want to slow down my CPU in my case to 800Mhz I could have specified the frequency manually, but I chose to do the following:

```
sudo cpufreq-set -g powersave
```

This has changed the mode to powersave, therefore my laptop is constantly running at 800Mhz and never goes over. The fan turns on once in a while, but for shorter bursts. I am affraid to go lower than 800Mhz (if thats even possible), but I do want the CPU to run cool enough so that I may cut off the fan.

I'm halfway there - Thank you MasterShrek

If anyone can confirm that you can set your CPU to something different than it's SET steps from the manufacturer please let me know.

:) happy happy joy joy

---

