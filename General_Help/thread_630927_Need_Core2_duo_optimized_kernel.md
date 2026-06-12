---
title: "Need Core2 duo optimized kernel"
date: 2007-12-03
forum: General Help
---

### Post by lifeontilt on 2007-12-03
Hi, I just installed Gutsy on a Dell Inspiron 6400 laptop which has an Intel Core2 Duo processor
I know that aside from the Generic linux kernel, I can optionally use the real time kernel that come pre-installed with Ubuntu Studio. My question is.... what are my options (if any other) for a possibly more optimized kernel as far as Intel Core2 duo processors are concerned. I am willing to compile my own as a last resort if need be.
Thanks for any help in advance. :KS

---

### Post by rfruth on 2007-12-03
My AMD x2 (dual core) saw (and uses) both cores no problem (fresh install of 7.10)

---

### Post by NotRoot:-) on 2007-12-03
You can specify the processor type  by compiling a custom kernel for your system:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
The url above is for the Master Kernel Thread that gives you step by step instructions.
I followed it yet again tonight and am now running 
uname -a
Linux YRUHere 2.6.23.9 #1 SMP Mon Dec 3 18:20:12 MST 2007 i686 GNU/Linux

I think the option you are looking for is listed under processor type and features as:

Core 2/newer Xeon (MCORE2)

Select this for Intel Core 2 and newer Core 2 Xeons (Xeon 51xx and 53xx)
CPUs. You can distinguish newer from older Xeons by the CPU family
in /proc/cpuinfo. Newer ones have 6.

---

### Post by lifeontilt on 2007-12-03
My installs fine and I can see the 2 cores, I was hoping for something a bit more optimized i guess. I will follow "notroots" advice and see what happens.

---

### Post by tgalati4 on 2007-12-04
Check out the gentoo forums.  The gentoo community is also putting out live CD's that are precompiled.  This saves you some time.  Perhaps there's a core2duo spin that you could try and install.

What kind of optimization are you looking for?  If you want more speed, try overclocking and shaving latency ticks from your memory.

---

### Post by Raven18940 on 2007-12-11
I have a very similar question, though I know the answer is to compile it myself.  My question is how?

I want to optimize my kernel for my CPU (AMD K8, but that's not really important), but I want an Ubuntu Kernel, not a Vanilla Kernel.  I read the Master Kernel Thread and compiled a Vanilla kernel, but it didn't work well, many drivers simply stopped working and you can forget the restricted drivers.  I don't need the latest driver support or any of the other reasons you'd compile the latest Linux kernel, I just want all my Ubuntu features to work right, but faster with optimized code.  So where do I get the Ubuntu Kernel source code as well the patches that need to be applied to it?  I know how to compile and optimize the code once I have those things.

---

