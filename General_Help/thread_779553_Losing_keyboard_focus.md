---
title: "Losing keyboard focus"
date: 2008-05-02
forum: General Help
---

### Post by Dhar on 2008-05-02
This problem cropped up when I upgraded to Hardy.  Just about any time a window or popup menu is opened, I stand a good chance of losing keyboard focus.  Let me give you a few examples that happen nearly all the time...

1) Open a Konqueror window, and begin typing in a URL.  The autocomplete popup opens, and suddenly I can't type any more.  The window has focus, but keyboard does nothing.  I have to click-raise a different window, then click back to Konqueror to restore the keyboard operation.

2) Opening an application (kate, a konsole, eclipse, etc.) will often result in that application not getting keyboard focus.  It has window focus, but I can't type until I select another window ala #1.

3) Alt-space brings up katapult, but I can't type anything.  It just sits there until I mouse over and off it, or click somewhere else.

I have a "Focus Follow Mouse" policy set, but that doesn't seem to make much difference -- I've always used that one, and using any of the others doesn't help this problem.

Is anyone else seeing this problem?  I'm using nVidia drivers, no compiz, one monitor, nothing different from a setup that worked just a couple weeks ago! :confused:

And a special note -- I lost keyboard focus once while writing this post. ](*,)

-g.

---

### Post by Dhar on 2008-05-07
Turns out it was scim doing all this.  I've uninstalled it, and no more problems!  Boo, scim!

-g.

---

### Post by BetterSense on 2010-02-19
This is STILL a problem as of February 2010. I had a debillitating bug with the Arduino program, pidgin, and everything else, but mostly the Arduino program. I thought it was java, tried everything. Glad I found this post. pkill scim and the bug is gone.

---

