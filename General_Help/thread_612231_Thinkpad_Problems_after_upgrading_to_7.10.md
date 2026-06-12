---
title: "Thinkpad Problems after upgrading to 7.10"
date: 2007-11-13
forum: General Help
---

### Post by onewhokills on 2007-11-13
After upgrading to 7.10 on my thinkpad t40, im having a bunch of problems, when i close the lid and then reopen it, the screen sometimes goes blank, and becomes unresponsive (it can be fixed by doing ctrl alt backspace), hibernate/suspend no long work...and somethines my keyboard becomes unresponsive (but my mouse/touchpad still work)

anyone know some easy fixes for my problems?


thanks for the help

---

### Post by Tigera on 2007-11-29
I could use some help here too.  I don't know where to start looking.  The machine was rock solid under Feisty, so Gutsy crashing on me was a nasty surprise!

---

### Post by cygnine on 2007-11-29
I've got a T60. The hibernate/suspend issue is a known problem with your ATI video driver (and mine, too). See [http://ubuntuforums.org/showthread.php?t=588239]("http://ubuntuforums.org/showthread.php?t=588239") for discussion and some workarounds. I haven't tried any of these, so I don't know what works. 

As for the lid closing and screwing things up, that could be caused by your power management set to suspend (which doesn't work) when you close the lid. Go to System->Preferences->Power Management to take a look.

I've had no problems with the keyboard, so I can't comment on that. It would be good for you to describe in more detail the keyboard problem so others can be more helpful.

---

### Post by Tigera on 2007-12-03
Actually, I have a HP dv8000 with an NVidia chipset in it.  I don't think that the ATI drivers are at fault in my case.  :)  
Sometimes, the screen will become blank even when the lid is open, or the laptop will lock up at random.

---

### Post by cygnine on 2007-12-03
See what happens when you assume....

Anyway, as that thread I linked to above points out, this isn't just a problem with ATI drivers. Some nvidia ones don't work, either. So I'd still read through that (sadly, long) thread. 

Also, there's a sticky to the thread [http://ubuntuforums.org/showthread.php?t=595825]("http://ubuntuforums.org/showthread.php?t=595825")
on the front page of this forum with a big list of known gutsy bugs. It's good to take a look at that for future problems. This bug is also reported there.

As for your screen randomly locking up/going blank, see what happens if you change your screensaver to just a blank screen. I had some display problems before I did this, and after switching to a blank screensaver, I have a lot fewer problems.

---

### Post by Tigera on 2007-12-03
Thanks for the pointers to the other threads, I'll read through them.  I don't believe my screensaver was set to anything but blank, but I changed it just to be safe.

---

### Post by hvac3901 on 2007-12-03
I havn't tried this yet, but i am planning on moving my laptop over to Ubuntu Gutsy 7.10 soon so i will be looking at this site for help, maybe one of you want to try it, it has almost all the thinkpad models and some known issues and how to fix them.

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_T61)

---

