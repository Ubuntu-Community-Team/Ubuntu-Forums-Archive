---
title: "Feisty problems - update manager and screensaver"
date: 2007-04-19
forum: General Help
---

### Post by Dave54 on 2007-04-19
I just did a brand new feisty installation (not an upgrade, a clean install). However, not even 30 min looking around and I have some problems.

First, a rather simple one: Update manager wants me to do an update. There're two updates, each for update manager itself. However, when I try to update, it says they're not authenticated. Should I go ahead anyway?

Second may be a bug. Please try this (in feisty) and tell me if the same happens to you (but save your documents first as they might be lost). Go to System > Preferences > Screensaver. Pick any screensaver and click the "Preview" button. Then click the "leave fullscreeen" button. At this point, gnome or something crashes as I'm immediately brought back to the log-in screen. Any open documents or programs are lost.

Thanks for the help guys.
-Dave

---

### Post by autocrosser on 2007-04-19
For the first problem: run sudo apt-get update in a terminal & then see if the updates are authenticated.

As for the second: 
1. I would file a bug on the package at Launchpad (check to see if there are any open bugs against Gnome-screensaver)  OR
2. disable Gnome-screensaver (I personally use Xscreensaver & still like it better) & re-enable Xscreensaver. There is a thread about this.

---

