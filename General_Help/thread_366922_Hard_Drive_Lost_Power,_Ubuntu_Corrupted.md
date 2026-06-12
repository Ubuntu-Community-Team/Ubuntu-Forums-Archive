---
title: "Hard Drive Lost Power, Ubuntu Corrupted"
date: 2007-02-21
forum: General Help
---

### Post by esaym on 2007-02-21
The other day I was poking around inside my computer and I touched one of the wires running to one of my hard drives.  I heard the hard drive shut off and then turn back on.  I didn't think nothing of it and I have had that problem for about a year now.  I never could figure out which wire has the bad connection or which hard drive was loosing power (I have 2, one sata and one pata).  I had always thought it was the sata drive that had the bad wire running to it.  It has never been too much of a problem since it only happens when you pull on the wires.

Upon closing up my case and sitting back down at the computer I noticed the screen had froze.  Now this was funny.  I also noticed the ide activity led was stuck on.  I opened the up the case again and started playing with the wires.  I heard one of the hard drives shut off and then turn back on again.  I looked back at the screen and moved the mouse and ubuntu was no longer froze.  This is good I thought.

So I figured while I had the case open that I would take the time to figure just which wire was getting the bad connection and which hard drive was loosing power.  I opened up syslog and noticed some errors being spit out by the pata drive.  I started playing with it and it while in the process of trying to find out which wire it was, the hard drive shut off and on several times.  I finally decided that the connector from the psu going to the pata drive was where the bad connection was.  Great! Now I can finally fix it and not have to worry about it.  I went to shut off ubuntu but it had locked up again.  Hmm. So I played with the wires and made the hard drive shut off and on a couple of times but it never made ubuntu unlock.  I waited for about 5 minutes before I finally forced the computer to restart.  The funny thing is I had always thought that the linux kernel could continue on without hard drive access so why did it lock up?  Anyone know about this?  Or maybe X just locked up and not the kernel?

Upon restarting, ubuntu went straight to the command prompt instead of X.  While staring at the screen and before I even had a chance to figure out what was going on, ubuntu restarted itself.  Again, it went to the command prompt.  I quickly logged in and did a startx.  Again however, ubuntu just restarted.  

I went ahead and stuck in the live cd and got it up and then ran e2fsck.  It spit out a bunch of errors on the sata disk, which is root and about 500 files ended up in lost+found.   The sata drive I thought wasn't loosing power.  I know the pata one was.  I didn't get any errors on any other disk or partition.  I thought all would be well but when I restarted ubuntu it just  did the same thing again (going to command prompt and restarting).

I finally said screw it.  I had another sata disk with a fresh back up on it.  I just stuck that one in and all was well.

I just really don't get what caused such massive corruption or data loss.  I had ext3 in data writeback mode instead of the default data ordered mode.  I am wondering if that is why?  Anyway I went ahead and set ext3 back to data ordered mode.  Hopefully I won't have this problem again.  

So far I can't tell the difference between data ordered and data write back mode.  Doing a transfer  from my sata disk to my pata one still pulls 7mbs-14mbs.  However when I was using ext2 doing the same transfer would get 45mbs-50mbs :-? 


I know this is a long post but does anyone have any comments on my my questions?  I am just trying to learn here :biggrin:

---

### Post by cookfromfrozen on 2007-02-21
Regardless of how you have the journal set up, if the hard drive loses power or the IDE cable falls out while the system is powered up, there is a high possibility for data loss and you can't really do anything about that.

You really shouldn't be tugging at your IDE / power cables while the system is switched on, but I'm sure you know that already.  IDE / power cables become looser as they get older and are easily knocked out just by touching them.

Occasionally, my hard drive makes a clunk, spins down and then back up, like if it has lost power.  The clunk sound is the head parking.  I am not exactly sure why it happens:  it could be the hard drive is going faulty, a bad IDE cable, unclean power / overloaded power supply, or the 4-pin molex connector might be loose.

In my case, I think it's the molex connector -- it's coming off a cheap 80mm fan (dumb setup I know) and is very loose.

---

