---
title: "Gutsy Recently Started to Suddenly Freeze"
date: 2008-06-21
forum: General Help
---

### Post by LordKelvan on 2008-06-21
Hi:

I have been using Ubuntu for about a year now, and things have been pretty stable.  However, in the last day, I have had Gutsy (7.10) suddenly freeze.  When it freezes, the mouse and keyboard no longer respond, and of course everything else stops.  I cannot restart X, or use the "magic" SysRq key combos to restart the computer.  I have to press the Reset button on my computer.

I have had no hardware changes for a very long while.  Internal temperatures are fine.  The first time Ubuntu froze, I was right-clicking Pidgin to shut it down.  The second time I was watching a movie full-screen.  The only recent software changes I remember were a minor kernel upgrade via synaptic (this occurred between the first and second crash, so I don't think its responsible) and a new version of Azureus (but the first time it happened I had already shut down Azureus < 1 minute before).

Can someone help me?

Thanks in advance,
Lord Kelvan

---

### Post by LordKelvan on 2008-07-13
Hi:

It happened again the other day - I had left my computer on overnight, with Azureus running, downloading stuff.  When I woke up, my computer was frozen.  After I restarted my computer (by pressing the physical restart button), I looked through the logs and couldn't see anything.

Can someone help me?

Cheers,
LK

---

### Post by Bubba64 on 2008-07-13
Very strange I have never seen a freeze problem on Gutsy.

---

### Post by kostkon on 2008-07-13
> **LordKelvan said:**
> Hi:

I have been using Ubuntu for about a year now, and things have been pretty stable.  However, in the last day, I have had Gutsy (7.10) suddenly freeze.  When it freezes, the mouse and keyboard no longer respond, and of course everything else stops.  I cannot restart X, or use the "magic" SysRq key combos to restart the computer.  I have to press the Reset button on my computer.

I have had no hardware changes for a very long while.  Internal temperatures are fine.  The first time Ubuntu froze, I was right-clicking Pidgin to shut it down.  The second time I was watching a movie full-screen.  The only recent software changes I remember were a minor kernel upgrade via synaptic (this occurred between the first and second crash, so I don't think its responsible) and a new version of Azureus (but the first time it happened I had already shut down Azureus < 1 minute before).

Can someone help me?

Thanks in advance,
Lord Kelvan

> **LordKelvan said:**
> Hi:

It happened again the other day - I had left my computer on overnight, with Azureus running, downloading stuff.  When I woke up, my computer was frozen.  After I restarted my computer (by pressing the physical restart button), I looked through the logs and couldn't see anything.

Can someone help me?

Cheers,
LK
It looks to me that you have a hardware problem.

Have you checked your logs for any messages? It may help you to understand what's wrong.

Some time ago I had similar crashes in 7.04 and I found out that it was a faulty graphics card. After replacing the card the crashes stopped.

I have upgraded to 8.04 since then.

Thus, it may be that you have a faulty part, for example your RAM or your graphics card, etc.

---

### Post by LordKelvan on 2008-07-13
As I mentioned in my second post, I have looked through the logs and don't see anything.  The logs that I've looked through are the ones available from the "System Log" menu entry.  Are there any other ones that may be helpful?

---

### Post by swordsmith on 2008-07-14
Hi, I've been experiencing similar reasons this past few days as well. I have a Dell Latitude D830. The first time I just had my computer in hibernation, with the screen-saver on, and then nothing would respond, forced boot was the only solution.
Then I was watching youtube, and then suddenly everything froze, with the last syllable of the video repeating over and over, forced reboot was the only solution.
Third time the same thing happened.
And just now, gutsy froze during screen-saver again.

The thing is, after all these reboots, nothing was broken...at least on the surface, all the applications ran smoothly as before, the freeze-ups are really unpredicatable.

The System logs didnt show any abnormal things, so I'm not sure what exact problem this is...

Another thing that I think might be of use is, when my computer froze the last three times, I had bittorrent running in the background...although I'm not sure how would that cause freezes.

---

### Post by bilijoe on 2008-07-14
This is a little too strange.  Just the other day I posted a message declaring that neither I, nor anyone else I know who uses Linux had ever had it freeze.  Later that night, gutsy froze solid on me.  I too had to resort to the power button on the console.  At least, somewhere in some "preferences" window, I had set the response to the console power button to be "shut down", so, at least I got an orderly shutdown and didn't loose any data.

Strange, but then, isn't life strange?

---

### Post by spen25 on 2008-07-14
WoW, I'm running Hardy 64 bit and just y'day and today I've been getting freezes and very sluggish performance while surfing. It has never happened before and I didn't make any changes.

---

### Post by bilijoe on 2008-07-14
I don't know what's happening, but I'll bet Bill Gates is behind it.:-$:roll:;):wink:

---

### Post by Jim! on 2008-07-14
Judging from all the posts it seems this is an issue with 7.10, Is there any reason why you can't just upgrade to 8.04.1? If its not an issue I recommend you upgrade. This is also proof that Ubuntu crashes which a large majority of the users seem to deny, Ubuntu has its own equivalent of the BSOD. Kernel Panics.

---

### Post by bilijoe on 2008-07-14
> **Jim! said:**
> Judging from all the posts it seems this is an issue with 7.10, Is there any reason why you can't just upgrade to 8.04.1? If its not an issue I recommend you upgrade. This is also proof that Ubuntu crashes which a large majority of the users seem to deny, Ubuntu has its own equivilent of the BSOD. Kernel Panicks. I've been considering upgrading, but I'm still hearing rumblings that some instability problems remain.  Re. Ubuntu crashing, I've been using it for a long time, some of my friends have been using it for years, and this is the first crash I, or any of my friends have encountered, and this thread contains the first reports I've heard of crashes.  I'm not saying it doesn't crash (not any more, at least), but crashes appear to be so few and far between as to be statistically irrelevant.  Anyway, no matter how you cut it, it does seem strange that there suddenly seems to be a rash of crashes (albeit small), all happening at roughly the same time, when 7.10 has been out there, running on, I presume, thousands of machines, for quite some time now, with no previous reports (that I know of) of crashing.  Maybe it's an astrological thing, or maybe some numerologist can enlighten us about something to do with the numbers involved in yesterday's date, or something.  It just seems too odd to be simple coincidence, to me.  I still think it's Bill Gates, in a darkened roomsomewhere, chanting and sticking pins in a stuffed penguin doll:mrgreen:.

---

### Post by Jim! on 2008-07-14
I too, never experienced Ubuntu 7.10 crashing and I was using it for at least a month after Ubuntu 8.04 was released. I suspect the crashing is probably due to a kernel upgrade that had issues with 7.10. 

As for 8.04 they 're-released' it fairly recently as 8.04.1 which is 8.04 with all the updates included. (Well a large majority of the updates since 8.04.1 was released more updates have appeared. Which is good because it means Ubuntu is constantly becoming better then it already is.) I think you should just give 8.04.1 a try since it seems to be very stable now and will most likely work better then your current 7.10 install.

---

### Post by LordKelvan on 2008-07-15
Well, it happened again just now, so I doubt it has anything to do with a particular date :D

I was just typing away at the console, and then it froze on me.  Again, I had Azureus running again - I don't know if this is part of the issue.  Just in case it is, I have enabled logging in the application.  Hey, swordsmith, which torrent client are you using (I'm asking just to see if maybe Azureus is the problem).

As for upgrading to 8.04.1, I have not because I have had a host of issues with 8.04.1 on another machine, including inexplicable (i.e., logs don't show anything) crashes :D  

Outside of upgrading, does anyone have other suggestions?  It seems odd that there would be a way for the kernel to crash, but without any log capturing an error message.

Cheers,
LK

---

### Post by LordKelvan on 2008-08-07
Well, I haven't experienced any more crashes - hopefully they were rare occurrences.  I'll keep you guys posted if it happens again.

---

### Post by Comhra on 2008-08-07
I'm running Gutsy as well and have experienced no freeze-ups.

Strange that there's a cluster of them right now for some users.

---

### Post by khangtoh on 2008-08-08
I too had been experiencing this lockup, its very random for my case. 

Sometimes I could be going for 5-6 hrs without a freeze and all the sudden it froze on me again. Sometimes it just freezes on me 20min after I reboot the system. It's getting to a frustrating state. 

I tried to upgrade to ubuntu hardy using update manager and it froze on me when it was update manager was starting up. So I don't really have the courage to upgrade through update manager, maybe a disc upgrade. 

Anyway, I turned off hyperthreading in my BIOs for now and will see if things get better.

---

### Post by nitramf82 on 2008-09-12
I have been experiencing this as well. Full freeze, no keyboard or mouse, nothing in the system logs that seems to help. Caps lock blinks. Sometimes it doesn't happen for days, sometimes it happens every 15 minutes.

I have especially noticed it on the video site hulu.com. If you need to troubleshoot this problem, I recommend going there. Usually about 10 minutes into a video the whole system will lock up. Its usually accompanied by the last moment of audio repeating until I hold down the power button. 

Only one time was I able to regain use of the keyboard and mouse after crashing, and the system was unstable with one of the CPUs stuck at 100%. This has also happened to me using Opera.

I originally thought it was a flash problem or a video card problem, but I've heard of this happening while using bit torrent, and for people using different video cards (I have the integrated intel one).  The only other thing I can think of is ndiswrapper - are you guys using this? Or possibly just wireless networking in general?

If anyone can tell me what I could monitor while trying to reproduce this issue, please let me know. The default logs in the GUI tell me nothing

---

