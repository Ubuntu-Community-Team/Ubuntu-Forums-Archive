---
title: "[SOLVED] top panel"
date: 2008-04-15
forum: General Help
---

### Post by dpwilson on 2008-04-15
I have a problem with my top panel.  After right clicking and selecting "add to panel", I tried to add tomboy notes and the system froze up.   A box came up saying something to the effect of "wait or force quit".  After waiting, I clicked force quit and my top panel basically became useless.  I cannot select anything as it is basically there for looks now.  I cannot use ALT+F2 to try and bring up a terminal.  The only way out is to use the pwr. button.

I just re-installed this system (7.04) and ran the updates.  After 198 updates downloaded, it hung up at "Setting up mono-gac (1.2.3.1-1ubuntu1.1) ...".  I never did get it installed , but did get around that error.

Is there anyway to reset it or fix this problem?

---

### Post by ryanhaigh on 2008-04-15
Change the a console by pressing ctrl+alt+f1, login and then ```
killall gnome-panel
```. The panel should automatically come back up.

---

### Post by dpwilson on 2008-04-15
Thanks, got it back and working.

---

