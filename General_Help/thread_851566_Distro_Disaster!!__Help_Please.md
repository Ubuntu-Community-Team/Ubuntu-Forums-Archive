---
title: "Distro Disaster!!  Help Please"
date: 2008-07-06
forum: General Help
---

### Post by toplaymusik on 2008-07-06
Ok, so I tried to update my Linux, I think I was using 6.04, and I tried to upgrade to 6.10 (step by step).  So when I opened up my software update manager, there was something like 815 updates.  So I attempted to update.  When I did so I was informed that I needed a "distro update."  So I did this.  It took like an hour to do, then when it was finished it said that it had failed, so I reopened  the update manager, this time instead of opting for the distro update, I just canceled that and checked the 815 updates and did this. This was much faster, but when it was finished, all of the dialog boxes that were supposed to say words, only had a series of little boxes on them, making it impossible to see what the computer was telling me.  So I restarted, when Linux came back up, the problem persisted, and my desktop had changed backgrounds.  No words, just boxes!  Something is seriously wrong, and I dont have much knowledge on how to fix.  Please help me and direct me as to how to solve this meddlesome problem.  Thank you.****

---

### Post by kuja on 2008-07-06
Sounds like a font related problem, maybe one of the font packages was removed?

Assuming you're using Gnome, run ```
sudo apt-get install ubuntu-desktop
``` and see if it installs anything.

---

