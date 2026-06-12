---
title: "Lost items in System &gt; Preferences"
date: 2008-06-03
forum: General Help
---

### Post by robz0rz on 2008-06-03
Dear community

A few days ago, I decided to clean up my System>Preferences menu a little by categorizing (much like Fedora Core). A day later (and a reboot later) I was surprised to see many of my System Preferences launchers in my Applications>Other menu. Without thinking much, I just deleted them. It only took me a few minutes to realize that they weren't in Sytem>Preferences anymore.  I must have misclicked at one point and moved them from my System>Preferences into my Application>Other menu. 

My question now is: Is there a way to get a list of my default launchers with command without booting another machine with my Live CD? Thanks for your time!


-- Rob

---

### Post by didac on 2008-06-04
Try:

```
alacarte
```

in a terminal

---

### Post by sdennie on 2008-06-04
alacarte should work.  You can also get there via System->Preferences->Main Menu.  Clicking the Revert button at the bottom should do what you want.

---

### Post by Sef on 2008-06-04
Alacarte has been renamed Main Menu (under System > Preferences)

---

### Post by robz0rz on 2008-06-05
I knew how to get into the main menu editor alacarte. The problem was getting all the commands back, they had been deleted (not just ticked off). I managed to boot my moms laptop with Ubuntu Live CD and transfered most of the menu entries back to my PC (by hand, I can't figure out where they are stored for the love of tux). The Revert option seems to be something I was looking for.

When I press it, will any installed programs that nested themselves in my Applications menu be gone? I'd rather not try it out...

---

### Post by sdennie on 2008-06-05
It looks like the revert menu will undo any changes and restore anything you deleted so, if you've put a lot of work into the menus and don't want to lose anything, it may not be exactly what you are looking for.

---

