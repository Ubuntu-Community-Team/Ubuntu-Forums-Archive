---
title: "powernap LoadMonitor threshold"
date: 2013-12-14
forum: General Help
---

### Post by pastim on 2013-12-14
I have been trying to get powernap to hibernate my desktop running 12.04 if it isn't doing anything, and not to do so if it is busy.  I have got this to work on user activity, and one or two specific processes. 
 
I spent quite a bit of time thinking it was monitoring changes to my configuration, as requested, but realised that some types of change were not being registered at all (eg I added an entry to DiskMonitor but nothing got monitored in the log), so I now stop and start powernap each time I make a change.

I haven't managed to get disk activity to 'not' work on my second disk (with my media files).  It always seems to be active.  I'm not greatly surprised since the config file does warn that even an idle disk is 'active' - it has to spin down and I'm not sure it does.

However, I was hoping to be able to use LoadMonitor as a backstop to keep the system alive when moving enormous files around, doing system backups etc.  The system is quite old, 2 * 2Ghz CPUs, 4GB memory.  The problem I have is that no setting of 'threshold' under LoadMonitor shows any activity at all.  To be honest I don't understand the explanation of what the values mean.  It is suggested that you specify 'n', and this will be set to the number of cpus.  I don't see how a threshold of 2 can mean anything with respect to load on a 2 cpu system.  Surely it isn't meant to be 100% for each cpu?  I have tried values down to 0.2, and up to 2, and n, to no effect.  The log (with full debug) shows it inactive at all times.  The part of the description that describes checking /proc/loadavg is also unhelpful to me, since this produces a string of numbers, some of which look like cpu loads, and others which must be something else.

So does anyone know how to make the LoadMonitor threshold work, and can they provide me with an explanation of precisely what the values mean?

---

