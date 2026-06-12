---
title: "indicator-datetime-service taking all resources"
date: 2016-12-08
forum: General Help
---

### Post by Dragonbite on 2016-12-08
I'm running Ubuntu 16.10 and found the system resources being all used up by indicator-datetime-service. When I mean all used up I mean 100% or RAM and CPU running at 100%!  

It stays up there for a few seconds and then 'drops' but I can watch as the RAM and CPU usage steadily increases.  Then there is an "out of memory" error and then the usage drops.

```
[  481.042518] Out of memory: Kill process 4752 (indicator-datet) score 853 or sacrifice child
[  481.042551] Killed process 4752 (indicator-datet) total-vm:6394096kB, anon-rss:3571212kB, file-rss:0kB, shmem-rss:0kB
[  481.382268] oom_reaper: reaped process 4752 (indicator-datet), now anon-rss:0kB, file-rss:0kB, shmem-rss:0kB
[  529.054660] signonpluginpro[4855]: segfault at 7faa8b425b98 ip 00007faa859b45df sp 00007ffe5c2913c0 error 4 in libQt5Network.so.5.6.1[7faa8591e000+16e000]
[
```

It seems to be connected with the battery power indicator.  When my laptop finished recharging the battery the issues stopped.

I had it set so the indicator would display the amount of time left to recharge/discharge so I went into the Unity Tweak and turned it off so doesn't display anything.  So far the system is not locked.

I just unplugged the chord and so far so good.  The indicator, however, hasn't updated to recognize it is unplugged.  I am hesitant to set it so the time left is displayed (though that is the preferred setting).

Has anybody seen this?  Is it because I used Unity tweaks?  

Ok, the battery indicates that it is discharging but I don't have the time displayed. I'm going to leave it this way and see if anything changes after a reboot or two.

---

### Post by epu on 2017-01-22
Did you ever figure out your issue?

I recently upgraded to 16.10 and I segfault about 2 minutes after boot, the last dmesg / kernel log print look very similar to yours (signonpluginpro/error in libQt5Network.so.5.6.1). I am having trouble in the few minutes of time I have before my system bricks figuring out what's causing the issue. I can boot from a 16.10 livecd and keep using the hardware without issue, so I may have to start rolling back versions of kernel/os components to match the livecd.

---

