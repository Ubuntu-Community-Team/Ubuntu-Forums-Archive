---
title: "Ubuntu 14.04 keeps resetting keyboard shortcuts"
date: 2014-06-01
forum: General Help
---

### Post by LifeEnemy on 2014-06-01
I'm a little disappointed in 14.04. Coming from 12.04, I was expecting less issues from an LTS release. Especially after waiting extra time before the upgrade.

Anyway, one of the problems I'm having is with keyboard shortcuts. I don't heavily customize them, but I'm highly accustomed to using Alt+F10 to toggle maximized windows. However, every few boots the system goes back to the old shortcuts. When I open keyboard shortcuts, they're all right back to their old settings and I have to set them all over again. How can I force Ubuntu to remember my keyboard shortcuts?? It's not a huge deal, but it's frustrating to reset them every few days.

---

### Post by LifeEnemy on 2014-06-06
Bump.

Is there some way to write a script that will reassign my shortcuts on startup?

---

### Post by LifeEnemy on 2014-06-07
I left my computer on overnight download files, and it seems to have reset my shortcuts overnight without a restart.

I also noticed that my custom shortcut (open system monitor with ctrl+alt+del) still worked this time, though it didn't seem to last time the shortcuts reset from a restart.

---

### Post by mc4man on 2014-06-07
This has apparently  been fixed in the latest compiz which is in 14.10.  Hopefully it will come to 14.04 via an SRU as it works fine trusty (using here in trusty 
The latest compiz has created a new bug while fixing something else but that's par for the compiz course
From changelog -

* Fix issue where custom keyboard shortcuts would get reset to defaults when rebooting or restarting Compiz. (LP: #1063617).

---

### Post by LifeEnemy on 2014-06-07
I saw a note on launchpad about that, but I couldn't figure out how to apply it. Unfortunately the discussions there are often too technical/curt/etc for me to easily understand.

So it sounds like it might be backported to the LTS sometime, maybe after they fix the new bugs?


Maybe I should just make the switch to Mint I've been considering for so long.

---

### Post by LifeEnemy on 2014-06-09
Is it possible to apply the fix now, or are we just stuck waiting?

---

### Post by daffy_ on 2014-07-03
I have a similar problem. I loose all my custom keyboard shortcuts (I really HATE a lot of the default ubuntu keyboard shortcuts, since they mask important keyboard shortcuts of IntelliJ)

And when I loose my own shortcuts on some of my reboots, re-configuring them is a PITA.

Fortunately someone have written a script to backup your current keyboard shortcuts and to re-store them from backup. So now my life is at least a little bit easier. :)

See here:
[http://askubuntu.com/questions/26056/where-are-gnome-keyboard-shortcuts-stored](http://askubuntu.com/questions/26056/where-are-gnome-keyboard-shortcuts-stored)

and look at the answer by Stephen Ostermiller.

---

