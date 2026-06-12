---
title: "overclocking and cpu scaling"
date: 2007-11-12
forum: General Help
---

### Post by dylanologist on 2007-11-12
I've overclocked my Core 2 Duo e4400 from 2.0GHz to 2.4GHz.  If I turn off Intel's SpeedStep technology in the BIOS, then the computer runs at the overclocked setting and this is reflected in the Conky system monitor I have on my desktop.  However, with SpeedStep left on in the BIOS, Ubuntu shows that the two cores of the processor never exceed the 2.0GHz limit they were designed to run at, even when I have the processor overclocked.

Ideally, what I would like is to leave SpeedStep on, but to modify the CPU scaling to allow a 2.4GHz maximum frequency.  Right now, the available frequencies are 2000, 1600, and 1200 MHz, all of which I would like to keep.  I only want the computer to run at the overclocked speed when it's really necessary (or useful, I should say).

I've found the location in the filesystem where these settings seem to be maintained:

/sys/devices/system/cpu/cpu0/cpufreq
/sys/devices/system/cpu/cpu1/cpufreq

Unfortunately, I can't seem to edit the files contained in this directory (and perhaps I don't want to if it's going to **** up my system).  Is there any way to modify CPU scaling in Ubuntu to allow for alternative frequency settings?

---

### Post by hikaricore on 2007-11-12
You should just disable SpeedStep and do your OCing in bios.

The files in /sys/ are not actual files and can't really be edited in the first place with any results.

---

### Post by Peturrr on 2008-03-07
Isn't it a bit strange to advise disabling speedstep, when on windows speedstep works with the OC values?

---

### Post by Fred_E _krugar on 2008-03-08
Not all MB will let you overclock and still have speed step(even if they say it is possible). In most cases the two do not play well together anyway.

---

### Post by Peturrr on 2008-03-10
Maybe I need to clarify my last post: I have the same issue and on Windows speedstep is working great with the OC values, but on linux it just uses the default speeds for speedstep, so the OC has no effect or use in linux.

---

