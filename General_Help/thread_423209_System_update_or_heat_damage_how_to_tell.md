---
title: "System update or heat damage: how to tell?"
date: 2007-04-25
forum: General Help
---

### Post by linuxgrrl on 2007-04-25
short version of my questions: Can excess heat slow down (as opposed to halt) a PC?   Alterantively: could updating my Dapper system have caused it to slow down, then  hang at the BIOS screen/refuse to boot?

Longer version / my sorry tale of woe:

I have a Dapper-based mythtv system on which resides my photos, music collection, tv recordings, etc.  It has run flawlessly for about 18 months with just a few reboots in that time.   I have not kept the packages up to date since Sept. 06 (when my son was born, no coincidence there).

So this past weekend I finally decide to perform a system update.  I uncheck all the packages that appear to have anything to do with mythtv (eg., mysql, etc.), not wanting to break something,  and hit "ok".   Uh oh, you know what comes next.

Next time I watch my mythtv the video is stuttering.  top shows seemingly normal results (I think ??)  ... mythtv using about 28-30% of the CPU while watching a live program, nothing else appears out of whack.  So I restart X, still stutters; restart system and ... it's completely DEAD!  Hangs at the bios screen for about 90 seconds, then reports "boot failure."  

Then I notice the case is quite hot (esp. the disk drives) and the case fan is not spinning (though the CPU fan is working fine).  So I'm guessing that heat is the problem.  But wouldn't heat would just "kill" the system (rather than slow it down first, then kill it??)  And why did this happen JUST when I did the system update ... is it possible it's not really the heat, but related to the update some how?  How could an update cause it to hang at the bios screen?

And most important, what now??  Can I get the data off these drives, or am I doomed? 

*snif* I miss my mythtv ....

---

### Post by rbmorse on 2007-04-25
From your description I would guess the hard drive has failed rather than the CPU.

---

### Post by jeffathehutt on 2007-04-25
Heat can cause a computer to slow down to a crawl.  With many newer CPU's, they have a smart sensor in them that will slow the processor down until it isn't hot anymore.  So, if your system is very hot, it is likely the processor would slow down to compensate.

It is highly unlikely that a software update could cause the system to freeze at boot.  If you happen to have a live cd handy, try booting with that.  That could at least rule out certain problems.

If the system still won't boot, it might be possible to get your files off the hard drive by installing the drive into another computer.  If the hard drive is damaged though, your data might be lost.

---

### Post by majoridiot on 2007-04-25
my first step would be to go into BIOS setup and reset it to default settings and then adjust from there.  it might also
allow you to view the cpu temp to see if something is screwy there.

if you can't even get as far as BIOS setup, check to see if there is a jumper on your mobo to clear cmos settings
and then try again.

as far as the update and all.. your video stuttering could have been caused from a kernel update that broke a 
proprietary (nvidia or ati) video driver.

if there was a "killer" in this situation, my guess is the heat.  if it was running constantly as you indicate, you could
have had a long-festering heat problem that *coincidentally* got ugly on upgrade.

---

### Post by AndrewNi on 2007-04-25
I would guess the hard disk drive myself. Drives often struggle when they're about to die, usually because they're trying to relocate sectors that cannot be read very well (causing the delays).

That's my guess, although the updates might be too much of a considence.

---

