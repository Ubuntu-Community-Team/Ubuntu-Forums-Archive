---
title: "Temperature"
date: 2016-07-04
forum: General Help
---

### Post by mafsi on 2016-07-04
Are this values, ok?:confused:
I modified my cpu governor from on demand to powersave.
Thanks in advanced!

---

### Post by banceu_sergiu_ione on 2016-07-04
Yes, they are. 
For more information you can also check, if you can find it, the sheet specification of your cpu and HDD/SDD on its respective to the hardware and check its operating temperature interval. Then from what Psensor output you have an idea if are good or not.

---

### Post by mafsi on 2016-07-04
Thanks a lot!

---

### Post by Linuxisfast on 2016-07-04
Corresponding to the CPU load, they are quite high. Have you cleaned your fan lately? Please install lm-sensors and do a sudo sensors-detect, say yes to all options and then reboot and see whats your fan rpm.

---

### Post by mafsi on 2016-07-04
> **Linuxisfast said:**
> Corresponding to the CPU load, they are quite high. Have you cleaned your fan lately? Please install lm-sensors and do a sudo sensors-detect, say yes to all options and then reboot and see whats your fan rpm.

I dont get rpm. i get only this:

```

[$]:[~]>> sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +78.0°C  (crit = +98.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +62.0°C  (crit = +100.0°C)
Core 1:       +60.0°C  (crit = +100.0°C)




```

---

### Post by pqwoerituytrueiwoq on 2016-07-04
78C is a bit high, but that may be normal for your cpu assuming the sensor is accurate
make sure the fan is spinning and it is not clogged with dust
unity can cause a continuous gpu load that makes laptop cpus read high temps as the commonly use the same heat sync, so the gpu heats the cpu
what is the cpu model?

---

### Post by mafsi on 2016-07-05
> **pqwoerituytrueiwoq said:**
> 78C is a bit high, but that may be normal for your cpu assuming the sensor is accurate
make sure the fan is spinning and it is not clogged with dust
unity can cause a continuous gpu load that makes laptop cpus read high temps as the commonly use the same heat sync, so the gpu heats the cpu
what is the cpu model?

This is my PC info, a part of it. I will check if my fan is clogged with dust , but only in two weeks. I will come with more info about it. Last time when i checked (4 month ago) it was ok. no dust.

```

System:    Host: xnbook Kernel: 4.4.0-28-generic x86_64 (64 bit gcc: 5.3.1) Desktop: Xfce 4.12.3 (Gtk 2.24.28)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: AOHAPPY2 v: V1.15
           Mobo: Acer model: JE06_PT Bios: INSYDE v: V1.15 date: 10/21/2011
CPU:       Dual core Intel Atom N570 (-HT-MCP-) cache: 512 KB flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 6650 
           clock speeds: max: 1666 MHz 1: 1000 MHz 2: 1666 MHz 3: 1000 MHz 4: 1000 MHz
Graphics:  Card: Intel Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1024x600@60.03hz
           GLX Renderer: Mesa DRI Intel Pineview M GLX Version: 1.4 Mesa 11.2.0 Direct Rendering: Yes
Sensors:   System Temperatures: cpu: 78.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A





```

---

### Post by T.J. on 2016-07-05
> **mafsi said:**
> Are this values, ok?:confused:
I modified my cpu governor from on demand to powersave.
Thanks in advanced!

That seems awfully hot, but your gear might be designed that way. 

[http://ark.intel.com/products/55637/Intel-Atom-Processor-N570-1M-Cache-1_66-GHz](http://ark.intel.com/products/55637/Intel-Atom-Processor-N570-1M-Cache-1_66-GHz)

I would make certain that you have a clean fan and if it has a heat sink that it is seated properly.

---

### Post by mafsi on 2016-07-05
> **T.J. said:**
> That seems awfully hot, but your gear might be designed that way.  Your processor is designed so that is possible to run that hot: [http://ark.intel.com/Products/Spec/SLB73](http://ark.intel.com/Products/Spec/SLB73)

I would make certain that you have a clean fan and if it has a heat sink that it is seated properly.

I do not mean to sound rude, but given that it is a 32 bit processor, if it were me I would be looking to replace it with a 64 bit gear before it becomes obsolete and impossible to get support.  Intel fabricates 32 bit hardware on the cheap, with the expectation that it is "throw away".   Most of the world switched to 64 bit over a decade ago, and some others have been 64 bit for over 20 years.

Most of the major versions of Linux plan to drop 32 bit support in the next few years.  When that happens, you will have to do updates yourself, by hand. That will only work for as long as the kernel developers maintain the i386-i686 branches, of course.

This is my processor. And it is on 64bit. However the netbook is quite old. 6 years old, and maybe that's why.

[http://ark.intel.com/products/55637/Intel-Atom-Processor-N570-1M-Cache-1_66-GHz](http://ark.intel.com/products/55637/Intel-Atom-Processor-N570-1M-Cache-1_66-GHz)

---

### Post by T.J. on 2016-07-05
> **mafsi said:**
> This is my processor. And it is on 64bit. However the netbook is quite old. 6 years old, and maybe that's why.

[http://ark.intel.com/products/55637/Intel-Atom-Processor-N570-1M-Cache-1_66-GHz](http://ark.intel.com/products/55637/Intel-Atom-Processor-N570-1M-Cache-1_66-GHz)


Yes, my apologies.  When I did the search for information on the processor, I made a typo, and got a much older model. GIGO, my friend. Garbage in, garbage out.  Bad information, bad analysis.

When I realized my error, I edited my note accordingly.  Next time, I will be sure to wear my glasses.  I would definitely check the hardware, and see if it needs a little maintenance.

Take care and the best of luck to you.

---

### Post by mafsi on 2016-07-05
> **T.J. said:**
> Yes, my apologies.  When I did the search for information on the processor, I made a typo.  When I realized my error, I edited my note accordingly.

Not a problem!
Tell me, T.J, will be a good idea to recompile my kernel in order to load only specs that are on my netbook? Sometimes I think that the default modules loaded with kernel will make a lot of process to run and I dont need them. Last time when I recompilend my kernel was 6 years ago on ubuntu 7.10 and my desktop (on that time) was loaded fast and run smooth. I'm not a specialist in linux, I'm only a simple user that knows some command lines, most of them taken from tutorials.
6 yrs ago, then I recompiled the kernel I used this tutorial : [https://www.howtoforge.com/kernel_compilation_ubuntu_p2](https://www.howtoforge.com/kernel_compilation_ubuntu_p2)
Will be ok, on 16.04 xubuntu?
Thanks in advanced.

---

### Post by T.J. on 2016-07-05
It may, but I suspect the benefits will be minimal, unless you can improve the kernel's process latency. That is VERY possible if the kernel was compiled with a lot of extra "crap" statically; but I would do that as the last resort.  If you compile the kernel yourself, you run the risk of breaking updates. Any kernel equal to or newer than the existing one should work, but you should be very careful, as newer kernels can have unforeseen bugs.

I've compiled much of Linux from scratch over the years and would be delighted to help you if necessary.  I'd try blacklisting the modules that you do not want loaded first, though.

---

### Post by pqwoerituytrueiwoq on 2016-07-05
I'm not very familiar with the Atom CPU series, but i find it hard to believe it is 78C under normal conditions, if that is the case, they went dirt cheap on the cooling system for it
make sure the fan is running, if it is not there is probably some kernel option required to get it working
it if does not run, see if it spins when viewing BIOS settings, if not id guess the fan failed and needs replacing

---

