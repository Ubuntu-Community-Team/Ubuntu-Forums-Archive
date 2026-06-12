---
title: "How to Recover An Account's Folders &amp; Files after Account is Poisoned?"
date: 2016-02-13
forum: General Help
---

### Post by oldefoxx on 2016-02-13
If only this much survives a a cut and chop, it will have to do:  Get file 001.txt at [https://my.pcloud.com/#page=filemanager&folder=63120803](https://my.pcloud.com/#page=filemanager&folder=63120803) and you can go from there.  Now here is the cut line:
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

I'm running Ubuntu 14.04, but this infection is generic.  Meaning it could hit any version or distro of Linux it seems.
But efforts to raise awareness run into pitfalls.  I have to phrase it as a question, not a warning.  Well, it is that too.

**How can I salvage all my  files and folders from my infected account? ** The infection is only to that account in terms of a setting of some kind, so I want the save to be of everything except settings that impact system packages like Nautilus, gedit, apt, apt-get, and even added packages like Slimjet.  It hits each a different way, like they lose some of their ability to do their job.  Even dfconf-editor lost the ability to display sone settings, like what should appear on the top panel in Metacity.  This is after Metacity, which started it all, quit working properly as well.

The losses are gradual.  dconf-editor did show the top panel, but on the next visit it didn't.  Launchers, some of them, quit launching.  Others would go later.  Portions of the top panel would just vanish.  Then the panels vanished.  Reinstalls came back to the same point.  Only by copying hidden folders and files from a working account over could I effect some bit of recovery, but it would not last.  And Metacity could not be uninstalled and it poisoned poisoned the other two interface options as well.  But the second account was fine, still able to use any of the interfaces with no problem.

It's not Metacity's fault.  There is some hidden weakness in Linux that was just exposed by Metacity, that's all.  And it exposed it simply by offering you the option to reposition the top and/or bottom panels.  If you do either, you will have an instant crash, a report sent off, and then the panel appears where expected.  But the crash that follows comes slowly, with one thing after another going bad.  And as I said, it starts with just that one account.  It could possibly go much further, and will, if you "salvage" your accounts and the flaw trigger goes with them.

My full report to date is in file 001.txt at [https://my.pcloud.com/#page=filemanager&folder=63120803](https://my.pcloud.com/#page=filemanager&folder=63120803)
I don't know what setting or what package or what library has the flaw.  I don't know what the crash report reported or whom it reported this too.  I stumbled onto a trigger and there may be others in other packages.  I'm not the person with the answers, but I have learned a lot about what doesn't work in trying to move beyonf this point.   That is what 001.txt tells you.  Read that, and you know almost as much as I do.  Not everything though, as I could not put words to everything, and am still learning more as I struggle to get my data and get free of this entanglement.

So again, one more time for those that just skipped through: ** How can I salvage just my stuff, meaning NOT system or applications settings or config files, but still get bookmarks, forms for Slimjet, password settings, email, address books, and things like that,  and bring them all over to my new user?**.  Then I can obliterate the old user and rename the new user as it were the old user.  Life back on track.

If you don't have a precise answer, please say nothing.   Like I said, I know a lot about what WON'T work, and even why in some cases,.  I would hate to have to refute your suggestions based on what I've learned for myself this last week of trying it all.  Everything I could think of trying anyway,

Consider me a proving ground.  You tell me, and it it hasn't been tried, I will try it.  I've nothing to lose at this point.  Then we will both know, and it might help others, now or later.  That's the best deal I can offer.  This is a loaded PC with hundreds of added packages, so I need some flexibility on what might be worth saving and what not to save.  I expect some give on both ends on that, mostly mine.  I can make the effort to get some of that on my own, and if what I learn here helps qualify me for doing it, that is even better.  Others will learn too.

Sneaky thought though:  What if this was a successful hack of Linux?  Whom would that benefit and how?  Just a possibility I suppose.  Might explain its worm-like behavior.  Intent would be an odd one though.  If a plant, why not just steal personal data and remain undetected?  It could only be to discredit Linux as a safe and secure operating system because it is revealedrepeatedly as it migrates throughout, and who would profit from that?  Some possible answers come to mind, but let the obvious speak for itself.

---

### Post by dragonfly41 on 2016-02-13
First, your posted link requires login details (username/password) so I haven't read 001.txt.

> How can I salvage just my stuff, meaning NOT system or applications settings or config files, but still get bookmarks, forms for Slimjet, password settings, email, address books, and things like that, and bring them all over to my new user?.

Given the scenario you have given I would

create a fresh user account and
import user profiles from "poisoned" user account to new user account, one at a time for testing.
~/.mozilla
~/.thunderbird
etc. (but changing ownership)

If you are really in a forensic mood use a package such as meld to compare differences in different user profiles (poisoned and new).

---

### Post by oldos2er on 2016-02-14
> I don't know what the crash report reported or whom it reported this too.

See /var/crash
There is some crash debugging info [here]("https://wiki.ubuntu.com/DebuggingProgramCrash").

You used the words "poisoned" and "infected" as if you suspect some malware was at work. Can you be more specific about why this might be the case, as opposed to something like hardware problems or software incompatibilities? A list of your hardware specs might help.

---

