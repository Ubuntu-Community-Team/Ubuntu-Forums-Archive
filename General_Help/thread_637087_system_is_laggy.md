---
title: "system is laggy"
date: 2007-12-10
forum: General Help
---

### Post by Kymus on 2007-12-10
This started just the other day, and I am unsure as to what exactly brought it on. Some tasks are slower than normal, and some skip a beat every few minutes (like ePSXe).

I tried rebooting, and that did nothing of course. I looked at the system monitor and 98% of the time, my CPU usage is up to 100% (with a few 70-80% down spikes here and there, but not constantly).

I have no clue what to do, how to investigate this, or even what other info to provide. :confused:

---

### Post by Flyingjester on 2007-12-10
system specs, and look in system monitor, are there any processes using large chunks of cpu?

---

### Post by xeth_delta on 2007-12-10
Open a terminal and use the command called **top**. It will show you what program is using so much CPU power. Are you perchance using beryl / compiz? There is a possibility that you do not have 3d ahrdware acceleration enabled and your CPU has to do a lot of graphics work.

Xeth

---

### Post by flamelab on 2007-12-10
What did you install lately ? Any wierd driver ? A program out of PMS ?

---

### Post by Kymus on 2007-12-10
> **Flyingjester said:**
> system specs, and look in system monitor, are there any processes using large chunks of cpu?

CPU:  	 AMD Athlon 64 3200+ Venice 2.0GHz
Video: connect3D 3038 Radeon X800GTO
Mobo: Foxconn NF4UK8AA
RAM: 1x1GB 2x512MB

looking at the Processes tab, there are only a few running processes that are higher than 0%:
[LIST]
[*]beagle & beagled-helper: between 5% and 35% (usually in the 20%, I'd say)
[*]firefox: 5% to 12%
[*]ktorrent: a steady 7%
[*]and when epsxe is running: usually around 60% [/LIST]

---

### Post by Kymus on 2007-12-10
> **flamelab said:**
> What did you install lately ?

nothin :-\

 > Any wierd driver ? A program out of PMS ?

I'm not a woman :P

---

### Post by flamelab on 2007-12-10
> **Kymus said:**
> CPU:  	 AMD Athlon 64 3200+ Venice 2.0GHz
Video: connect3D 3038 Radeon X800GTO
Mobo: Foxconn NF4UK8AA
RAM: 1x1GB 2x512MB

looking at the Processes tab, there are only a few running processes that are higher than 0%:
[LIST]
[*]beagle & beagled-helper: between 5% and 35% (usually in the 20%, I'd say)
[*]firefox: 5% to 12%
[*]ktorrent: a steady 7%
[*]and when epsxe is running: usually around 60% [/LIST]

Stop beagle , it causes problems to me as well . Try that and then tell us what happened .

---

### Post by Flyingjester on 2007-12-10
I think it's pretty obvious epsxe is eating up your resources.

---

### Post by Kymus on 2007-12-10
> **xeth_delta said:**
> Open a terminal and use the command called **top**. It will show you what program is using so much CPU power. Are you perchance using beryl / compiz? There is a possibility that you do not have 3d ahrdware acceleration enabled and your CPU has to do a lot of graphics work.

Xeth

Compiz gives me a white screen, see me signature ;P

---

### Post by Kymus on 2007-12-10
> **Flyingjester said:**
> I think it's pretty obvious epsxe is eating up your resources.

It's run fine without skipping up until 2 days ago

---

### Post by Kymus on 2007-12-10
> **flamelab said:**
> Stop beagle , it causes problems to me as well . Try that and then tell us what happened .

I will try that

---

