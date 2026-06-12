---
title: "12 year veteran Linux user asks: How do I debug a crashing laptop?"
date: 2007-09-06
forum: General Help
---

### Post by mogul on 2007-09-06
So after a dozen years of using Linux, promoting it, customizing it, etc. I am ashamed to admit: I have no idea how to diagnose what is causing my beloved Linux laptop to crash.

My laptop crashes about 3-5 minutes after I take it off adapter power. It didn't always do this, but started a couple of months back. In general, picking up my laptop to go to a meeting has become a nervous exercise.  The first impression many people get of me and my Linux laptop is to see me having to reboot it before I can get anything done in the meeting... So much for positive impressions.  My epic uptimes are a thing of the past. :(

I used to think it had something to do with also unplugging a wired cable and letting NetworkManager roll me over to wireless at the same time, but have now eliminated that as a variable.

When it crashes, the cursor freezes in X, the system monitor applet stops updating, the hard drive light is lit but it doesn't sound like the drive is thrashing... In general, everything is frozen.  CTRL-ALT-F1 to try to get a terminal doesn't work.  A single push of the power button does not work.  The only recourse I have is to hold down the power button for four seconds and cold boot the machine.

The big problem now is that I've no idea what to investigate next or how.  As this usually happens at meetings, it's not like I can easily try SSH'ing into it.  So: What do you do when cold-booting a machine that crashed to figure out what went wrong?  Is there any log that will survive such a hard crash?  What can I do to figure this out?  How will I know if it's a hardware problem? It seems crazy to me that I don't know what to do next after such a long time as a Linux user, but maybe it's just that I've always had such great stability that I never had to learn how; there was always a way to recover and see what was going on, even if was by killing X.  

Anyone have pointers?

---

### Post by rbmorse on 2007-09-06
How old is the battery? They have a finite service life.

---

### Post by lightstream on 2007-09-06
> **rbmorse said:**
> How old is the battery? They have a finite service life.

That was my first thought, but it wouldn't freeze the machine, just kill it.

I would tend to think hardware though; the one time I had linux freeze was due to a faulty connector on my DVD making intermittent contact.

Is it completely stable when on mains power?

---

### Post by TravMan63 on 2007-09-06
Does the computer go into a 'power saving mode' just before it halts?
(i.e. screen dimming, processor switching to slow speed?)

I've seen resolution changes halt a laptop...

--
I did have problems with network manager not allowing a boot up when a cable was plugged in.... but haven't seen your problem.

I use wicd for networking now - works better from what I've seen.

---

### Post by PilotJLR on 2007-09-06
Do you have anything interesting or unique in /var/log/messages before the times when a freeze occurs?

---

### Post by mzilhao on 2007-09-06
are you using feisty fawn?
i have similar issues with feisty on my desktop. occasionally, it just completely freezes.
see this thread for more info: [http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)
i do hope gutsy will fix these issues, otherwise i'll have to give fedora 8 a try. my feisty is just as unpredictable as windows me...

---

### Post by louistan3 on 2007-09-06
you might have loose connections like on your harddrive maybe? or maybe the RAM? 

i think thats where you should look first.. try to remove any accessories so you could isolate

the problem..

hope this helps :)

---

### Post by trippinnik on 2007-09-07
You said it started a few months back? Do you know if it corresponded with a kernel upgrade?  Have you tried booting the previous kernel?  
The only time I had a similar problem was because I was trying to use the open source ATi driver with 3d accel on my legacy mobile gfx.  It would freeze like that at random intervals after coming out of sleep.  Can you give us a bit more info about your hardware?

---

### Post by scrooge_74 on 2007-09-07
I had something similar starting yesterday, but only at a friend's office, not at home or anywhere else.

First I was thinking it started after installing sane and sane-utils.

But checking /var/log/message something that pops up just before a freeze is this line

*ACPI: Unable to turn cooling device [de31f9b4] 'on'*

any takes on this? My system is a nx6110 not the best laptop around, but it takes me places, I am running Ubuntu 7.10

---

