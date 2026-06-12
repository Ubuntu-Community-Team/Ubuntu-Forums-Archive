---
title: "Start a specific screensaver from a launcher"
date: 2007-08-03
forum: General Help
---

### Post by Frinky on 2007-08-03
Hello,

I want to create a launcher that will start a *specific* screensaver (skyrockets actually - my son likes watching it).

After searching on the net, I found a way to create a launcher to start the *current* screensaver. The command is:

gnome-screensaver-command --activate

However, this only starts the current screensaver. If I change Ubuntu's screensaver it will no longer show rockets. How can I create a launcher that will always show the skyrockets screensaver? Would it be best to launch the skyrockets application directly (if this is even possible)?

Thanks,
Frinky

---

### Post by Frinky on 2007-08-04
I've discovered what I want to do.

Rather than start the screensaver I can just call skyrockets directly. Created a launcher to:

/usr/lib/xscreensaver/skyrocket

Does the trick nicely.

I had considered writing a script to change the current screensaver setting to rockets, running the screensaver, and on exit setting the current screensaver back, but the simpler solution is, well, simpler.

---

