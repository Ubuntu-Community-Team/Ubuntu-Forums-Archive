---
title: "&quot;roll back&quot; updates - possible?"
date: 2008-05-15
forum: General Help
---

### Post by Thanh-BKK on 2008-05-15
Hello :)

Please excuse me if this is a stupid question, but does Ubuntu (Hardy Heron 8.04 here) have a Windows-ish feature like "last known good configuration" or similar, which would allow to "roll back" a botched update?

I am just a little paranoid - i made Ubuntu my sole OS and i am still very new to it, it works perfectly but every day (!) there are many (!!) updates coming in, way more than i ever had with any Windows-version, and i know for sure that updates, while mostly being good, can also screw up a running system.

Like today, when i had to reboot after an update (and i thought only Windows does that - nope, Ubuntu does, too!) the boot got stuck at around 25% of the progress bar for several minutes before it continued - i almost panicked. Then also AWN didn't start (it was one of the things that got updated). However after starting it (AWN) manually and reboot once more everything was fine again, to test i repeated that a few times (like 5-6 more reboots, always with power off inbetween) and all was well.

Still i would like to know if there is (or can be installed) a possibility to simply revert the last updates in case the system refuses to boot or has some other new bug that wasn't there before the update.

Or is it possible to just stop the "update" process altogether, as they say - never change a winning team, if my system has no visible bugs and runs perfect, why update? 

Please advice...... thanks in advance :)

Thanh

---

### Post by Bubba64 on 2008-05-15
> **Thanh-BKK said:**
> Hello :)

Please excuse me if this is a stupid question, but does Ubuntu (Hardy Heron 8.04 here) have a Windows-ish feature like "last known good configuration" or similar, which would allow to "roll back" a botched update?

I am just a little paranoid - i made Ubuntu my sole OS and i am still very new to it, it works perfectly but every day (!) there are many (!!) updates coming in, way more than i ever had with any Windows-version, and i know for sure that updates, while mostly being good, can also screw up a running system.

Like today, when i had to reboot after an update (and i thought only Windows does that - nope, Ubuntu does, too!) the boot got stuck at around 25% of the progress bar for several minutes before it continued - i almost panicked. Then also AWN didn't start (it was one of the things that got updated). However after starting it (AWN) manually and reboot once more everything was fine again, to test i repeated that a few times (like 5-6 more reboots, always with power off inbetween) and all was well.

Still i would like to know if there is (or can be installed) a possibility to simply revert the last updates in case the system refuses to boot or has some other new bug that wasn't there before the update.

Or is it possible to just stop the "update" process altogether, as they say - never change a winning team, if my system has no visible bugs and runs perfect, why update? 

Please advice...... thanks in advance :)

Thanh 

In synaptic there is a history of updates from there but I am not sure if it shows download updates. You can stop updates by going to software sources either in synaptic or system administration and change the update status.  I have never had a update mess up my system you see them on here because this is where people come for help, and they are a extremely small in amounts compared to everybody using Ubuntu.

---

### Post by forestpixie on 2008-05-15
You can change the updates so that you only get security updates, also chnage it so that it either downloads or notifies you - gives you a chance to check out updates before you apply them. So you could check the forum to see if others have had problems with updates.

Have you got backports and proposed enabled? If you have I would disable them if you need to make sure your machine carries on working, there is a possibility that you could have problems with those repos.

You can do these in software sources.

Generally ubuntu will need to restart if there have been kernel updates - most other things will update even if you're using it.

It is possible to lock software at a version with synaptic - I did it with gutsy when I installed the openoffice version rather than using the ubuntu version.

---

### Post by Thanh-BKK on 2008-05-15
Hello again :)

Thank you both for the replies. 

@Bubba64: 
I meaned when an update botches my system, for example it downloads something that screws up X or whatever and i end up with a system that doesn't boot, i can always get a recovery mode CLI from Grub. I am looking for a way to "go back" from there, i.e. uninstall any recent update (most recent ones) :)Because if the system still boots so that i can get to Synaptic, , well, i don';t have too much of a problem - as a mouse pusher i'm still worth my money, however if it comes to command lines i am still fairly new at it :)

@forestpixie:
Right now my system is set (stock? I never changed that) to display a red triangle with exclamation mark when there are updates available. I click that and it opens up the update manager, which then shows me all available updates and asks me if i want to download and install them. So far, i have allowedthat every time, thinking "updates must be good as Hardy is still quite new" but the little hiccups today sounded an alarm bell for me and now i think - system works fine, better NOT update anymore before it ends up NOT working. 

About the repos, if the ones you mentioned (backports and proposed) have to be enabled manually, then i don't have them. I know for sure i got "universe" and "multiverse" (or are they the same that you mentioned??) enabled, plus one non-ubuntu repo for AWN (something -bzr), i'm going to disable that one as soon as i get home. I am now at work, on a Windows box :) 

With kind regards.....

your Thanh

---

### Post by forestpixie on 2008-05-15
That all sounds ok then - it's probably worth just casting an over updates before you allow them.

Which updates have you had which have caused you problems - because it could be worth looking into them if for no other reason than it migh need a bg reporting if it hasn't already been.

---

### Post by Thanh-BKK on 2008-05-15
Hello again :)

Now i'm back home, sitting in front of my Ubuntu box. I have just checked all the details i was given here - the "Backports" and "Proposed" repos were not enabled, and i disabled (un-checked) the "AWN" ones (it was four actually, not just one (ppa.launchpad.net.... repos), while they are surely not bad repos i am more happy if my 100% functioning AWN is left untouched :)

I am not that overly concerned about security either - i am the sole user of this computer (my boyfriend doesn't want to learn Linux.....) and there is no material on the machine that would be interesting for any hacker - and i trust in Ubuntu "out of the box" already being more secure than Windows anyway :)

Still i have set the updates now (via Synaptic) to only get the "Important Security Updates" and i will check periodically for other updates manually, like when i happen to find a bug :)

As to todays updates, there were 14 of them of which 3 were for AWN, i am sorry but i don't remember what they all were... is there a way to find out? Such as "update history"? I'm sure there is a log file somewhere... but i'm still green behind the ears, Ubuntu-wise. 

Again i wish to thank you very much for your help, please if you also know an answer to the first question (roll back possible?) please let me know... thanks in advance :)

With kind regards.....

Thanh

---

