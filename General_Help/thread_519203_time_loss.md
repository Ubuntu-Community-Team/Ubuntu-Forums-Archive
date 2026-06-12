---
title: "time loss"
date: 2007-08-06
forum: General Help
---

### Post by bearcat on 2007-08-06
At some point within the past 24 to 48 hours, my Ubuntu installation started reporting the time incorrectly. I had to be somewhere at 9 p.m. Sunday night, but I didn't get there until 10 p.m. because by 9:30 real time Ubuntu was reporting 8:45 and I didn't realize I was late. I resynced the time before I left; by the time I got home at 1 a.m. Ubuntu had already lost 15 minutes again. So I resynced again before I went to bed at about 3 a.m. -- and when I woke up this morning at 11, Ubuntu was reporting the time as 10:15.

The computer wasn't turned off at any point during this period, so it's not a boot problem, and I *do* have the correct time zone selected (I checked, twice.) 

So I logged out of Ubuntu and booted into Windows this morning. The Windows clock was initially set to the same erroneous time as Ubuntu, but I resynced in Windows and left my computer running for the day while I went out running errands. Got home about 15 minutes ago, and the Windows clock was still reporting the correct time. I've just checked, and Windows did *not* automatically resynch itself to a time server while I was out -- which means this isn't a hardware problem, but something Ubuntu is or isn't doing correctly. Any advice?

---

### Post by apetresc on 2007-08-06
Hey, bearcat.

In some cases, faulty power management for the processor can cause time skews like this. Try disabling all the ACPI/cpu scaling features from your boot sequence and see if it still happens.

As a temporary salve for the problem's symptoms, though, you could have Ubuntu use NTP to resynch the clock every, say, hour, to a time server.

---

