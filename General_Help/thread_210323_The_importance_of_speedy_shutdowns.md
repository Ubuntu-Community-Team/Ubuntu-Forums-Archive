---
title: "The importance of speedy shutdowns"
date: 2006-07-06
forum: General Help
---

### Post by regeya on 2006-07-06
True story from July 4th.

It was a lovely...scratch that, rainy 4th of July afternoon.  Well into the rain, I started hearing a significant amount of thunder.  "Uh, I should unplug stuff," I said.  I went to my main desktop machine and started shutdown, then went to unplug:

[LIST]
[*]The TV
[*]The stereo equipment
[*]The DVD player
[*]The microwave in the kitchen
[*]The coffeemaker
[*]The mixer
[*]My phone from the charger
[*]The camcorder charger
[*]My wife's computer
[/LIST]

And by then, shutdown was *almost* complete.  By the time init was done and the machine was about to shut down, I saw a blue flash and heard a loud ***POP***!

:-k

Fortunately, the house didn't burn down, but the phone box outside the house was blown across the yard, the security alarm was toasted, and the power bar was toasted.  Since I live in the country, the only affordable Intarweb option was dialup, so the modem may be toasted; I've not tried it yet as we didn't have a dialtone until our alarm was fixed.

Now, to the best of my knowledge, this brush with Mother Nature will only (only!  single income right now with property taxes and car insurance about to wipe out our savings...oog, the joys of parenthood) run between $300-$400; unfortunately, with a $500 deductible that'll be a lot of paperwork for the insurance company *and* it'll all be out of our pocket.

And sure, had the computer been fried,  insurance would have covered replacing the equipment.  Sure.  And of course I have backups.  In all seriousness, I have everything in /home backed up except .mp3s and video files.  So I could restore that and install Kubuntu easily.  That's not the point.  The point is that this would have been avoided had the machine shut down relatively quickly when kdm halted the system.

OK, so no more excuses, guys.  No anectdotes about how big iron often takes minutes to hours to start up and shut down.  No stories about how server boxes need their sanity checks.  No witty stories about Windows XP or OS X boxes that take minutes to shut down.  **Those are all irrelevant**.

The important question is this:  Given that Ubuntu is aimed at end users, and that end users (in my experience, at least) often just want their computers on when they want to use them*, why does it take an act of Congress to shut down?  Why leave it to the savvy user to install init-ng with its overly-simplistic init scripts?

Sorry for this turning into a rant, but dealing with insurance agents, phone company people, and others is starting to wear on me.  :-D

*if you're power-usage-conscious like me, or if, like me, you've ever had a computer **catch fire while you sleep**, you'll understand the desire to shut down during idle time.

---

### Post by Maggot on 2006-07-06
Off or on, plugged in I would assume it will fry either way no?

---

### Post by T700 on 2006-07-06
[quote=regeya]OK, so no more excuses, guys.  No anectdotes about how big iron often takes minutes to hours to start up and shut down.  No stories about how server boxes need their sanity checks.  No witty stories about Windows XP or OS X boxes that take minutes to shut down.  **Those are all irrelevant**.[/quote]

So a freak accident that caused you a problem is a reason to make speeding up the already quite fine (by my standards) shutdown process a priority?  Just how often do you expect end users to race to the ramparts to save their systems, with seconds to spare?  

I hate to sound unsympathetic, but there are about 63,782 other things I'd like to see the developers work on first.

Paul

---

### Post by nameiwantistaken on 2006-07-06
If my electronics were threatened, I would use the express method of yanking the power cord/phone cord from the wall.  Where do you live?  Texas or Oklahoma?  I've never seen rain like the rain in Texas.

From my limited experience with Ubuntu, start and shutdown times are fairly long.  They're about on par with say Windows 2k, but the Vole put a ton of resources into closing down the boot up time for XP, so I'm sure it would take a concerted development effort on the part of the linux and GUI (Gnome, KDE, etc) people to make this timing issue shorter.  Hunt around though, I'm sure some people have ideas on how to hack your system to shorten things up.  There likely isn't an easy way to do it though.

On a side note, you should probably scrimp up to buy one of those all in power bars so that anything connected to your machine goes through the one place.  Plenty of people use a power bar to protect their machine, but forget that a lightning strike will probably send a nice zap of electricity through the phone line too.  This will help in case the lightning comes while you're asleep at work.

---

### Post by aysiu on 2006-07-06
[QUOTE=regeya]
OK, so no more excuses, guys.  No anectdotes about how big iron often takes minutes to hours to start up and shut down.  No stories about how server boxes need their sanity checks.  No witty stories about Windows XP or OS X boxes that take minutes to shut down.  **Those are all irrelevant**.

The important question is this:  Given that Ubuntu is aimed at end users, and that end users (in my experience, at least) often just want their computers on when they want to use them*, why does it take an act of Congress to shut down?  Why leave it to the savvy user to install init-ng with its overly-simplistic init scripts?[/QUOTE] I don't see why you're entitled to make generalizations about shutdown time based on your anecdote, but you don't want other people's anecdotes.

I could very well say that because my computer takes only 10 seconds to shut down that everybody's does. That's essentially what you're doing--saying that everyone's Ubuntu takes minutes to shut down just because yours does.

---

### Post by Al3xanR0 on 2006-07-06
[QUOTE=aysiu]I don't see why you're entitled to make generalizations about shutdown time based on your anecdote, but you don't want other people's anecdotes.

I could very well say that because my computer takes only 10 seconds to shut down that everybody's does. That's essentially what you're doing--saying that everyone's Ubuntu takes minutes to shut down just because yours does.[/QUOTE]

One can't help to ask how the shut down procedure is being performed. Have you considered circumventing shutting via menu, by typing  ```
sudo shutdown now -h
``` or ```
sudo halt
```? Or is machine just dog slow? If so shoot the dog, yank the power cord man! Providing you aren't performing any heavy tasks; EXT3 journaling is pretty good at restoring integrity, hence the reason why it is the default FS on most GNU/Linux distros.

---

### Post by regeya on 2006-07-06
T700:  Lamest.  Excuse.  Evar.  Try again. :-D

Aysiu:  My anecdote is related to Ubuntu Linux.  Stories about big iron (which invariably come up when startup/shutdown times come up) are not.

And the length of startup/shutdown is related to the number of services running, yes.  However, I have a comperable number of services running on a 7-year-old OS X box, and it starts up in a heartbeat and shuts down in a few seconds.  And let's take a look at the complexity of launchd vs. the Debian/Ubuntu init scripts.

I don't claim to have all the answers; I was looking to see if anyone else had thoughts on the subject other than 'STFU n00b WORKSFORME CLOSED WONTFIX'.  Guess not. :-P

---

### Post by sternael on 2006-07-06
A few years ago, I used Windows 2000 almost daily and the slow booting was a real hell, it ended with me booting normally once a week and hibernating the rest, saving lots of time.

However, W2K had the fastest shutdown I've seen on any OS, with ACPI enabled and assigning the power button, the computer stops in 2-3 seconds, and that is a controlled shutdown, not a pull-the-plug solution.

I think that Ubuntu still suffers from the server thinking.

---

### Post by K.Mandla on 2006-07-06
Is it just me, or is pressing the power button a quicker way to shut down than using the menu?

---

### Post by squeky on 2006-07-06
How about a UPS?  We had a lightning strike in the yard a couple weeks ago.  Power went out as soon as it hit and the monitor turned all green (it doesn't turn green running off the battery).  Hit the degauss button and problem solved.  May have sucked bad without that buffer in between.  Seriously, EVERY computer should have a UPS.

---

### Post by T700 on 2006-07-06
> **regeya said:**
> T700:  Lamest.  Excuse.  Evar.  Try again. :-D

<snip>

I don't claim to have all the answers; I was looking to see if anyone else had thoughts on the subject other than 'STFU n00b WORKSFORME CLOSED WONTFIX'.  Guess not. :-P

Searching for similar complaints indicate that it isn't a very common problem with people.  If you want to respond in a constructive manner great.  If you want help speeding up your shutdown process, I'm happy to help.  

Paul

---

### Post by ProjectGod on 2006-07-06
don't know about everyone else... but i find that most users... especially at work never really shut down their machines. even normal office users... some just log off... some don't even log off! they don't enable their power saving options either... 

we had an electrical storm and all the CRT monitors were ruined.

---

### Post by woedend on 2006-07-07
a) if you are in that big of a hurry I'd just kill the xserver (ctrl alt backspace) then manually shut if off and unplug.  
b) its not hard to speed up startup/shut down by using sysv-rc-conf to remove services to quicken the boot process...then deleting stuff out of runlevels 0 and 6 folder to speed up shutdowns and reboots.

---

### Post by tsb on 2006-07-07
You just need better wiring and surge protection.  Time to call an electrician.

---

### Post by Bokonon on 2006-07-07
While I feel for you (I lost a HD in a lightning strike), I would say that the best thing would be a good surge guard.

That way it won't matter if you are away or within reason, your shutdown time.  With a good quality manufacturer, they often have a replacement warranty should the surge guard fail.

Since my incident, I make sure that my important systems are behind a surge guard that I am confident in.  I have a UPS for some things, but my SLI power supply is too much for it.

---

### Post by Hairy_Palms on 2006-07-07
my windows xp loads in 43 seconds ubuntu loads in 45 
xp shuts down in 18 seconds ubuntu shuts down in 30 
i tihnk 30 seconds is perfectly reasonable shutdown time...
ive done no editting with any boot time speeding up things, only thing i ddid is uninstalled pcmcia and bluetooth support.

---

### Post by 3rdalbum on 2006-07-07
Ubuntu's shutdown time is ridiculous, and definately needs some love. There are probably tons of services that could be just killed, rather than "cleaned up".

But I've had Windows XP shutdowns (without performing updates) which have been slower.

---

### Post by Hairy_Palms on 2006-07-07
what sorta shutdown times are we talking about here?

---

### Post by Culito on 2006-07-07
3 hours.

Just kiddin'

---

### Post by jimmygoon on 2006-07-07
Sorry but you can't compare Ubuntu to Mac OS X unless you can get it running on all the PC (archs) that Ubuntu supports.

I thought it was a wonderful story but maybe rather than generalizing and being kinda rude to the Ubuntu devs, you save your files and yank the cord or buy a power strip or shut down your computer earlier...

I'm a bit confused as to why the computer caused all the problems... How did the computer getting fried affect your other stuff ???

---

### Post by Paulus on 2006-07-07
the power button method sucks because when u reboot it checks all your drives.  Which isn't fun if you've got half a terrabyte of data.   The shutdown times are really slow, and to be honest i don't understand the need for half the stuff it does,  is it crucial to unmount (for instance) volumes before it's reset by the bios? :-?

---

### Post by jimmygoon on 2006-07-07
> **Paulus said:**
> the power button method sucks because when u reboot it checks all your drives.  Which isn't fun if you've got half a terrabyte of data.   The shutdown times are really slow, and to be honest i don't understand the need for half the stuff it does,  is it crucial to unmount (for instance) volumes before it's reset by the bios? :-?

if it didn't unmount the volumes then it would want to check the HD again, thats the point of unmounting it (and data corruption which is rare anyways)

you can hit "Ctrl+C" and stop the check at the next boot up... either way, its better than having you 500 gig HD fried cause you were waiting to avoid a check disc ;)

---

### Post by Paulus on 2006-07-07
yeah, your right of course.  But how can windows get the job done in literally 4 seconds on my setup.  unfortunatly with ubuntu it's a hell of a lot longer why?  This wasnt the case with breezy ,  I have been skipping the disk checks because **i turn my computer on to use it, **not to wait about.


it seems that (in my eyes) after logout.. unmounting harddrives is the only thing that needs to be done before shutdown, what else needs to be done and why?

---

