---
title: "live streaming get stuck"
date: 2015-02-27
forum: General Help
---

### Post by nadeemohd1 on 2015-02-27
I am using emachine e527 and i have problem in live streaming like live tv channels and watching videos on youtube. If I dont use the laptop and turn on the youtube and lesson songs and after sometime when i try to access the system the system will not respond but the songs still continus so the only solution with me is to power off using the power button 
I think it have some problem with my graphic card when i was using 12.04LTE at that time it was working fine but now in 14.04 LTE I dont know what this problem is and why it is not support.
If any suggestion help me

---

### Post by TheFu on 2015-02-28
That machine uses a Celeron 900 CPU (687) which is very slow.  You need to offload the video processing to a modern GPU to get any streaming application to work ... or turn down the resolution to be DVD quality (480p) - really anything less than 720p should work if the machine isn't busy doing other things.  I have a similar performance AMD APU system, but it does video processing for mpeg2 and h.264 video in the GPU, so hidef content isn't an issue for the slower CPU.

So - what GPU does the machine have? None is listed in the specs.
**sudo lshw -C video**  will tell us.

---

### Post by nadeemohd1 on 2015-03-17
how to turn down the resolution

---

