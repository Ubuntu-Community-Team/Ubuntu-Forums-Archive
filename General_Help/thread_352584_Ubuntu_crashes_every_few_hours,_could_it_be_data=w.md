---
title: "Ubuntu crashes every few hours, could it be data=writeback?"
date: 2007-02-03
forum: General Help
---

### Post by tnunamak on 2007-02-03
My computer keeps crashing a couple times a day, even when the machine is idle. I'm not sure what's causing it to crash, I didn't see anything suspicious in /var/log/syslog. Could it be having changed the filesystem to use data=writeback? I did it using the following page: [http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed).

I also overclocked my processor around the same time, but I turned it back down to what I know is a safe speed that I've used in windows for weeks.

I want to be careful about assuming it's one thing or the other, what's a good way of tracking down the cause of the crashing?

---

### Post by glabouni on 2007-02-03
> **tnunamak said:**
> I want to be careful about assuming it's one thing or the other, what's a good way of tracking down the cause of the crashing?

simple. revert writeback to ordered state. if it still crashes then it's the O/C thing.

---

### Post by tnunamak on 2007-02-03
I changed both the file system and the processor to their original states, and it has still crashed twice in the last few hours.

I'm not sure what the problem could be. Any help?

---

### Post by tnunamak on 2007-02-03
Windows has been running for about 5 hours now and it hasn't crashed, so I'm fairly certain it's not a hardware issue.

---

### Post by glabouni on 2007-02-06
it is not that simple, as different OS make different use of hardware.
anyway I don't think your problem is hardware. if your ubuntu went from stable to crashy, try to remember what you've changed in the meantime and reverse it.

---

### Post by georgew on 2008-04-17
Windows will run on systems that are known to crash under linux.  

So just because it ran windows does not mean it will run linux.

Turn the overclocking all the way off, and see if linux stops crashing.
If you cannot restore normal operation after turning overclocking off, 
you may have damaged a system component by causing it to overheat 
when overclocked.  That, or you have overlooked something that is still 
tweaked.  See if the bios has a failsafe mode that has conservative settings, 
if so use it to see if linux will run.  If it does, you can slowly turn one setting 
up at a time to see exactly what setting is causing the crashes.

I appreciate your need for speed, but in many cases performance is already 
at it's limit in critial parts of the system, so overclocking results in unreliable
operation.  Overclockers trade ocassional crashes for speed.  If you want to 
avoid crashes, you probably should not be overclocking.

Ever have a windows machine that is acting strange, and it is fixed by a reboot?
sometimes that is caused by a hardware problem...  Instead of detecting an error
and crashing, windows will continue to run with corrupted data.  The same event
is likely to have crashed a linux machine.  So flakey hardware can run windows 
better than linux.  I have seen that proven over and over.

It is very possible that a machine that runs windoes "fine" is still broken
and cannot be used to run linux.  I have two such machines in my slag-heap.
It is not uncommon.  Sometimes they will run linux fine untill you add one
more thing.  For example, one of my systems is a vmware server, and
the first client runs fine, but a second vm client will crash in 2 hours.
But it runs windows perfectly.  All of my other, identical, vm servers can run 
a half dozen fully loaded clients without ever crashing.

The point is hardware faults that don't crash a system until you apply 
new software are common.  It can be the system load, or a normally
unused system part.

Overclocking can be pushed harder on lightly used systems, but a common
failure point for overclocked systems is overheating a critical part
because of an applied load.  things run warmer on busy systems, and
the design of linux allows more work to be done, so a greater demand for 
cooling is possible.


George

---

