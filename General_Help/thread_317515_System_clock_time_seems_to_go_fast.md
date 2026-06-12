---
title: "System clock time seems to go fast"
date: 2006-12-12
forum: General Help
---

### Post by veraction on 2006-12-12
My system's clock time seems to go fast. If I leave my computer on, the system time gradually seems to become too late. If I restart my computer, it goes back to the actual time (thus, my actual motherboard's system time is correct? or no?). For every 7 days of uptime, my clock seems to gain about 24 minutes into the future. Anyone have any idea why this would happen?

I've had this problem ever since Hoary. And I've done fresh installs of Ubuntu during that time. 

I've tried that "Keep clock synchronized with servers" feature, in "Adjust Date & Time", but I didn't notice any changes.

I suppose it must be hardware related?

---

### Post by mcduck on 2006-12-12
If the CMOS battery on the motherboard is dying it usually causes computer's clock to run fast.

The battery is a small flat one, usually located around the lower right corner of the motherboard. When it runs out of power you'll have to reconfigure your BIOS settings every time you start the computer.

Of course if your computer is only year or two old it's unlikely that the battery is the problem. If your computers BIOS shows the time you could try leaving it in BIOS for some time to see if the time will go faster there also.

---

### Post by veraction on 2006-12-12
Yes, I was thinking that this might be the problem. Though, I thought that it wouldn't be the case because of how the system time is set to the correct time after restarting (and not the same, fast time). But, perhaps there is some feature in Ubuntu which automatically corrects the system time on startup, but not on other times.

Thanks, I'll look into buying and replacing this battery, and see how it goes

---

### Post by medpowell on 2007-08-13
I see something similar since upgrading 6.10 to 7.04.

Just upgraded from 6.10 where everything was fine. Now in 7.04 the system clock runs two times fast. E.g. adjtimexconfig wants to set ticks=5000 instead of expected 10000.
This is with 2.6.20-16-generic.

If I reboot and select the previous kernel, 2.6.17-12-generic, the system clock runs correctly.

System is HP/Compaq Presario, AMD Athlon64 Processor 3200+, 1024Mb RAM.

---

