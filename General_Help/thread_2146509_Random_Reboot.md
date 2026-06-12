---
title: "Random Reboot"
date: 2013-05-18
forum: General Help
---

### Post by petsoukos on 2013-05-18
Hi,

I'm experiencing random reboots with Ubuntu 12.04. The computer is running normally and then randomly shuts it's self off and reboots. I've checked the logs that had a timestamp of last modification a few seconds before rebooting. There was nothing unusual being recorded, although some didn't include timestamps for their rows of data So I don't know what to make of them. How can I pinpoint the problem if there aren't any logs of what happened?

I've already run a memory test, but there were no errors.
There is an issue with the GPU fan speed, which doesn't automatically adjust according to temps, but I manually set the fan speed to 45%. Since I'm not running any 3D stuff, with 45% fan speed the temps are holding around 41-44C. (I think the desktop environment is using some GPU, but it doesn't push the temps any higher than 50C)

Also, is there a way to record the last 10 temp outputs of my GPU in a log file with the watch command?
```
watch -n 1 aticonfig --od-gettemperature
```


My specs:
[LIST]
[*]Intel i7 920@3.05GHz (OC'd) (normal temps, stable on Win8, never had a BSOD)
[*]6GB DDR3 Tripple Channel @1250Mhz (downclocked)
[*]AMD/ASUS 6870 1GB (stock clocks) with proprietary FGLRX (post-release updates) drivers
[*]SSD 128GB (main) + 250GB HDD (storage)
[/LIST]

I'm with Ubuntu for a couple of weeks, I used Mint as a VM installation on a Win8 host for quite some time, but I want to run Linux as my main OS now. Btw, I did install Mint 13 first and had the same reboot issues and switched to Ubuntu for that reason. But reboots still occur, although less frequent compared to Mint.


P.S.
Sorry for any bad grammar. English isn't my native language.

---

### Post by mrajdl on 2013-05-18
> **petsoukos said:**
> Hi,

I'm experiencing random reboots with Ubuntu 12.04. The computer is running normally and then randomly shuts it's self off and reboots. I've checked the logs that had a timestamp of last modification a few seconds before rebooting. There was nothing unusual being recorded, although some didn't include timestamps for their rows of data So I don't know what to make of them. How can I pinpoint the problem if there aren't any logs of what happened?

I've already run a memory test, but there were no errors.
There is an issue with the GPU fan speed, which doesn't automatically adjust according to temps, but I manually set the fan speed to 45%. Since I'm not running any 3D stuff, with 45% fan speed the temps are holding around 41-44C. (I think the desktop environment is using some GPU, but it doesn't push the temps any higher than 50C)

Also, is there a way to record the last 10 temp outputs of my GPU in a log file with the watch command?
```
watch -n 1 aticonfig --od-gettemperature
```


My specs:
[LIST]
[*]Intel i7 920@3.05GHz (OC'd) (normal temps, stable on Win8, never had a BSOD)
[*]6GB DDR3 Tripple Channel @1250Mhz (downclocked)
[*]AMD/ASUS 6870 1GB (stock clocks) with proprietary FGLRX (post-release updates) drivers
[*]SSD 128GB (main) + 250GB HDD (storage)
[/LIST]

I'm with Ubuntu for a couple of weeks, I used Mint as a VM installation on a Win8 host for quite some time, but I want to run Linux as my main OS now. Btw, I did install Mint 13 first and had the same reboot issues and switched to Ubuntu for that reason. But reboots still occur, although less frequent compared to Mint.


P.S.
Sorry for any bad grammar. English isn't my native language.


i had the same thing with my system, it was the power supply over heating

---

### Post by petsoukos on 2013-05-19
> **mrajdl said:**
> i had the same thing with my system, it was the power supply over heating

Well I wasn't experiencing anything a couple of weeks ago with Windows, but I'll give it a good clean just in case.

---

### Post by mrajdl on 2013-05-19
> **petsoukos said:**
> Well I wasn't experiencing anything a couple of weeks ago with Windows, but I'll give it a good clean just in case.

In my case a good cleaning was to late, I took the cover off the power supply and inside was had brown smoke stains all over, coming from a reset-able fuse.  When my system rebooted I would here a click, the same click as if I powered down.

A visit to Ebay and $35 later new power supply with 100 more watts, runs great...

---

### Post by petsoukos on 2013-05-30
I gave my PSU a good cleanup a few days ago, but it wasn't really clogged with dust. I also run the memory tests again and additionally I run a Linpack benchmark without causing any reboots. I could clearly hear the PSU fan picking up speed indicating the system was serious load.

Here is also the benchmark result for anyone interested.
```

CPU frequency:    3.050 GHz
Number of CPUs: 1
Number of cores: 4
Number of threads: 8


Parameters are set to:


Number of tests: 1
Number of equations to solve (problem size) : 20000
Leading dimension of array                  : 20000
Number of trials to run                     : 4    
Data alignment value (in Kbytes)            : 4    


Maximum memory requested that can be used=3200404096, at the size=20000


=================== Timing linear equation system solver ===================


Size   LDA    Align. Time(s)    GFlops   Residual     Residual(norm) Check
20000  20000  4      119.912    44.4837  3.917629e-10 3.467960e-02   pass
20000  20000  4      119.061    44.8019  3.917629e-10 3.467960e-02   pass
20000  20000  4      119.800    44.5255  3.917629e-10 3.467960e-02   pass
20000  20000  4      120.485    44.2723  3.917629e-10 3.467960e-02   pass


Performance Summary (GFlops)


Size   LDA    Align.  Average  Maximal
20000  20000  4       44.5208  44.8019 


Residual checks PASSED


End of tests

```

[COLOR=#ff0000]Clearly, it isn't a PSU issue. Maybe a GPU issue?[/COLOR]

---

### Post by petsoukos on 2013-05-31
Can't recreate the reboot. It happens mostly while browsing (Chrome) and usually the exact moment I click on a link or a tab.

I also did a stress test of the GPU today. It reached 81C, but I got worried and canceled it. I let it run for about 6-7 minutes without reboot/crashing.

---

### Post by mrajdl on 2013-05-31
> **petsoukos said:**
> Can't recreate the reboot. It happens mostly while browsing (Chrome) and usually the exact moment I click on a link or a tab.

I also did a stress test of the GPU today. It reached 81C, but I got worried and canceled it. I let it run for about 6-7 minutes without reboot/crashing.

IF it doesn't seem to be hardware, why not replace Chrome with Chromium.

---

### Post by petsoukos on 2013-06-01
> **mrajdl said:**
> IF it doesn't seem to be hardware, why not replace Chrome with Chromium.

I didn't know there was a difference. I think I'm running chromium, I've installed it through Ubuntu Software Center.

---

### Post by mrajdl on 2013-06-01
> **petsoukos said:**
> I didn't know there was a difference. I think I'm running chromium, I've installed it through Ubuntu Software Center.

There's not much difference, both are fast, Chrome by Google is based off of Chromium.

In an earlier post:

"I'm with Ubuntu for a couple of weeks, I used Mint as a VM installation on a Win8 host for quite some time, but I want to run Linux as my main OS now. Btw, I did install Mint 13 first and had the same reboot issues and switched to Ubuntu for that reason. But reboots still occur, although less frequent compared to Mint."

Ok 2 different flavors of Linux with the same problem, and the logs not catching anything????  What else could it be, well It could be a ton of other conflicts ect....

Maybe the cleaning to the PSU was enough, you'll find out soon enough.

Let me know I'm curious.

Mike

---

### Post by petsoukos on 2013-07-04
That's embarrassing...

I cleared the BIOS to its default settings a week ago and haven't had any reboot since. I guess Linux didn't agree with the overclock. Windows probably is more tolerant with overclocking since I extensively tested the overclock settings there without issues. I'll keep monitoring for any reboots.

EDIT.
I should also mention that I switched the graphics card driver (the one that ubuntu installs) with the official from AMD.
I also can't tell if a software update fixed my issue (kernel upgrade or something).

---

