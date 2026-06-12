---
title: "Software Update running at every log in..."
date: 2014-09-15
forum: General Help
---

### Post by MrMichaelHill on 2014-09-15
I've noticed recently that software updater is running every time I log on! This only used to run once a week?

I have changed the settings for Software Updater to check for updates Weekly & under 'Session and Startup' I have even un-ticked 'Update Notifier'

But still every time I log in it checks for updates, even when it doesn't find any. If I log off and back on right now it will check again :-(

I only want it to check once a week, Its not a big issue I know but its really bugging me!

Thanks! 

Xubuntu 14.04

---

### Post by mcduck on 2014-09-15
That's actually exactly what it's supposed to do. 

The setting is only about how often you want to be *notified* abut available updates. The updater runs at every login since any important security updates should be installed as soon as possible, and the updater will also always show any critical updates to you immediately when they are availabe. Then if there aren't any critical updates, it'll wait based on your preferred setting before bothering you with the normal updates.

(and yes, of course it will check for updates even if it doesn't find any. How would it know if there are any updates available if not by checking for them?)

---

### Post by MrMichaelHill on 2014-09-16
Yeah I get that it has to check each day, However it never used to do this I'm sure?! Or am I going mad?

---

### Post by mcduck on 2014-09-16
You might be going mad then :D

I'm absolutely sure the updates have always been checked at least every day... Are you actually seeing the Software Updater window or are you just noticing it in the runnng processes? If it's displaying the window then there of course is something strange going on.

---

### Post by MrMichaelHill on 2014-09-23
Its displaying the window everytime I log in. Pops up in the middle of the screen "Checking for updates"

Edit: I'll get a screenshot when I get home!

---

### Post by MrMichaelHill on 2014-09-23
Right...

This opens every time I log in. even if I log off then log straight back in?

[IMG]http://i62.tinypic.com/2cnfozc.png[/IMG]

---

### Post by pfeiffep on 2014-09-23
> **MrMichaelHill said:**
> I've noticed recently that software updater is running every time I log on! This only used to run once a week?

I have changed the settings for Software Updater to check for updates Weekly & under 'Session and Startup' I have even un-ticked 'Update Notifier'

But still every time I log in it checks for updates, even when it doesn't find any. If I log off and back on right now it will check again :-(

I only want it to check once a week, Its not a big issue I know but its really bugging me!

Thanks! 

Xubuntu 14.04

I just checked my situation about software updater - running Ubuntu 14.04.1 with gnome flash-back using metacity.  

I had an security update notification on first login which I accepted - once installed it required a reboot. 

After the reboot and successful login I immediately logged out and and back in - I did NOT notice software updater running.

---

### Post by Michael_McKenney on 2014-09-23
My updates are set daily.  How can I run them manually instead?  This box is not left on and I turn it on to run the tape drives only.  I don't mind upgrading after the backups are done.  I don't want them triggering on startup.

---

### Post by pfeiffep on 2014-09-23
Look at:[INDENT]System Settings
     Software & Updates
          Updates Tab
[/INDENT]
You should be able to uncheck and choose 'never'

---

