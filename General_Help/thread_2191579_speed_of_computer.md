---
title: "speed of computer"
date: 2013-12-03
forum: General Help
---

### Post by rdema19403 on 2013-12-03
i have Ubuntu 12.04 ls on my system it seems to be running slow is their any thing i can do to make it run quicker  like defrag the hard drive on some type of preventive maintenance ?
Thanks in advance

---

### Post by Impavidus on 2013-12-03
How slow is "slow" and what are the specs of your machine? CPU, RAM, graphics card. It could be a graphics driver issue. Maybe there are better proprietary drivers available.
Linux doesn't need a lot of maintenance, except for the occasional clearing of old kernels. And that's only for disk space, not for speed.

---

### Post by aromo2 on 2013-12-03
Run Task Manager and check the memory usage (click on View and UNCHECK "Show memory used by cache as free").  If the memory usage is close to the total RAM (say 80% or more), you likely need install more RAM.

---

### Post by deadflowr on 2013-12-03
> **aromo2 said:**
> Run Task Manager and check the memory usage (click on View and UNCHECK "Show memory used by cache as free").  If the memory usage is close to the total RAM (say 80% or more), you likely need install more RAM.

What's task manager?

---

### Post by philinux on 2013-12-03
Maybe he meant system monitor.

---

### Post by deadflowr on 2013-12-03
> **philinux said:**
> Maybe he meant system monitor.

Yeah, I'm thinking that too.
I know task manager in Windows which has SOME similarities to system monitor.

To the OP, has the slowdown been recent or has it been like this for a while?
Have you installed anything new?

---

### Post by rdema19403 on 2013-12-03
these are the specs
	
225-2785
Vostro V2420 BTX Laptop
1
319-0665
Intel Celeron Dual Core B820 1.7Ghz Vos
1
317-9412
2GB, DDR3, 1600MHz, 1 DIMM Vostro
1
331-3410
Keyboard with Gesture Touchpad, English Vostro
1
320-3172
14.0" High Definition (720p) LED with Anti-Glare Vostro
1
320-3232
Intel HD Graphics/HD Graphics 3000 Sandy Bridge Vostro
1
421-7213
Dell SRV Software 1703/1704,BT,E/C MLK Vostro
1
342-4272
320GB 5400RPM SATA Hard Drive Vostro
1
318-1895
London Slate Vostro
1
421-7122
UBUNTU 11.10 Linux
1
430-0608
Integrated 10/100/1000 Network Card Vostro
1
318-1894
8X DVD+/-RW Dual Layer Drive Vostro
1
430-4667
DW1703 802.11b/g/n, BT4.0 Vostro

---

### Post by rdema19403 on 2013-12-03
no nothing new it is a laptop have not added anything

---

### Post by philinux on 2013-12-03
It would help if you define or categorise what slow means to you.

---

### Post by jdeca57 on 2013-12-03
> **rdema19403 said:**
> no nothing new it is a laptop have not added anything

If it was always slow you could try XFCE (Xubuntu) and you can install that alongside ubuntu and compare the speed. And if that is satisfying you can try Xubuntu next upgrade or install.
It's simply a fact that all modern Linux versions look towards the future and are a bit less forgiving for, let's say, not so recent hardware specifications.

---

### Post by Impavidus on 2013-12-04
RAM is decent, graphics shouldn't need additional drivers. Your processor and HDD are a bit slow, which is not uncommon for laptops. Ubuntu 11.10 is unsupported, I recommend changing to 12.04 or 13.10. Maybe change to Xubuntu. But still, how slow is it? It may be all you can get on that laptop.

---

### Post by jboyette on 2013-12-04
i would suggest installing cpufreq-utils and indicator-cpufreq  to change the frequency used.  I have had celeron processors automatically default to the lowest frequency...  and this application allowed me to 'bump' it up

---

