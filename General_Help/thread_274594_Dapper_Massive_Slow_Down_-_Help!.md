---
title: "Dapper Massive Slow Down - Help!"
date: 2006-10-10
forum: General Help
---

### Post by robbobkirk on 2006-10-10
Hi,

I've installed Ubuntu on an IBM P4 desktop machine and initially everything is ok. However, after a few days and always in the morning after it's been left on all night the machine is deathly slow.
I've tried putting the stock 2.6.18 kernel on and that does the same.

The CPU itself is not busy and nothing appears to be using the disk. I've checked /proc/cpuinfo and everything looks normal in there. I've checked dmesg and /var/log/messages and can't see anything.
I've disabled the screensaver and that had no affect.
I did an hdparm however and that returns extremely slow figures.

What else do I need to try? 

SuSe 10.0 was running on the machine before with no issues so I don't think it's a hardware fault.

Help!

Rob

---

### Post by mssever on 2006-10-10
Sounds to me like a dying hard drive. The hard drive might have gone bad *after* you removed SuSE. If you dual boot, you can verify whether or not the hard drive is at fault by checking if the other OS is slow. You could also boot from a live CD and try copying files to see what speed you're getting.

I hope I'm wrong about the HD.

---

### Post by robbobkirk on 2006-10-10
Thanks for the reply.

I can't see it being a dying hard drive. It's run for several days without issue. I've rebooted this morning and all is ok - as it always is after a reboot.

Also I would have thought 'dmesg' would have shown some disk problems - I managed to check that before I rebooted.

---

### Post by nikhilk on 2006-10-10
Just guessing here, maybe the memory is running low. Next time you encounter the problem check the output of the "top" and "free -m" commands. That should help diagnose the problem.

---

### Post by robbobkirk on 2006-10-10
Hi nikhilk,

I checked that as well, and also checked the swap. The machine has got 1Gb of RAM and 2Gb of swap. After removing the buffers/caches there was about 1/2 Gig Free and the swap wasn't being used.

Rob

---

### Post by nikhilk on 2006-10-10
Ok, I guess we can rule out "low memory" as a possible cause then. Sorry I cant think of anything else though.

---

### Post by megamania on 2006-10-10
> **mssever said:**
> Sounds to me like a dying hard drive. The hard drive might have gone bad *after* you removed SuSE. If you dual boot, you can verify whether or not the hard drive is at fault by checking if the other OS is slow. You could also boot from a live CD and try copying files to see what speed you're getting.

I hope I'm wrong about the HD.
Yes, the hard disk or the motherboard hard disk interface could be the problem.

When the computer starts slowing down, press ctrl+alt+backspace and see what happens. If the machine still works very slowly or shows "strange" messages regarding ATA/SATA writes, then that's likely to be the problem.
If you are able to go to terminal mode without a problem, then you probably have a software problem (lucky you!).

Of course, there could be other causes - I'm just trying to help from my personal experience.

---

