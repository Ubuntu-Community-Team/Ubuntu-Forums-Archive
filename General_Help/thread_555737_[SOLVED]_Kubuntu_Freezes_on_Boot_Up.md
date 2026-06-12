---
title: "[SOLVED] Kubuntu Freezes on Boot Up"
date: 2007-09-20
forum: General Help
---

### Post by Pikestaff on 2007-09-20
Background information: I use Kubuntu 6.06 and have been using it exclusively with few problems for the past eight months.

Anyway, I was going about my normal computer stuff today and decided to reboot because I noticed that the automatic updates were being kind of odd and not working right.  So I went to the menu and restarted the computer.

It starts to load up okay but then after it should be all loaded up (the progress bar is at 100%), the Kubuntu logo pops up again with a blank progress bar and everything just freezes.  I waited about ten minutes to see if it would do anything, but it didn't.  Rebooting again got me the same problem.

I can get into recovery mode so I guess that's a good sign but I'm not sure what to do from there.  Currently I've got a LiveCD in and am running fsck/checking for bad blocks and hoping that will fix it.

But I wanted to see if maybe any of you guys had any ideas on what happened or how to fix it?  I really hope fsck fixes it (it's fixed a lot of things for me in the past) because if it doesn't I'm not sure what to do :( any ideas?

---

### Post by Pikestaff on 2007-09-20
Okay, fsck didn't work :( If anybody has any ideas please let me know, or else I'm going to have to figure out a way to get my files and then reinstall...

---

### Post by dabl on 2007-09-20
When it appears to be "frozen" -- partial logo/progress bar or whatever, and shows no movement at all, try Alt-F1, and if that doesn't do anything, try Ctrl-Alt-F1.

If either one of those switches you to the console (Command Line Interface aka "text prompt"), then your problem is a hosed video driver.  Why?  I have no clue!  :)

So, reinstall it using whatever method is suitable, and you should be good to go another 2 years!

:lolflag:

---

### Post by Pikestaff on 2007-09-20
> **dabl said:**
> When it appears to be "frozen" -- partial logo/progress bar or whatever, and shows no movement at all, try Alt-F1, and if that doesn't do anything, try Ctrl-Alt-F1.

If either one of those switches you to the console (Command Line Interface aka "text prompt"), then your problem is a hosed video driver.  Why?  I have no clue!  :)

So, reinstall it using whatever method is suitable, and you should be good to go another 2 years!

:lolflag:

Alt+F1 got me to a command prompt and let me log in... what do I do exactly if I have a video driver problem?  The LiveCD was running just fine...

---

### Post by dabl on 2007-09-20
Here's your ticket: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:guitar:

---

### Post by Pikestaff on 2007-09-20
> **dabl said:**
> Here's your ticket: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:guitar:

Okay, I reconfigured xorg a couple times and it didn't work at first but it seems to have got it working now.  The first couple times it wouldn't boot KDE, gave me messages like "could not start ksmserver" and told me I didn't have permission, so I think something must have messed up with permissions somehow but I seem to have gotten it fixed thanks to chmod.  So it's working fine now!

HUGE THANKS for pointing me in the right direction!! :KS

---

### Post by dabl on 2007-09-20
> **Pikestaff said:**
> 

HUGE THANKS for pointing me in the right direction!! :KS

You are quite welcome.

Yes, be careful about the "permissions thing" until you've got the hang of it.  It's VERY different from Windows, in that regard. Do_ not_ yield to the tempting notion that if you merely do everything as "root", that somehow the permission issues will be avoided.  You can actually hose up your system beyond recovery doing that.  :guitar:

---

