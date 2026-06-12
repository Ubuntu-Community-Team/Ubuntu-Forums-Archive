---
title: "Beryl Partyl Working"
date: 2007-02-02
forum: General Help
---

### Post by nhandler on 2007-02-02
I have Beryl installed on Ubuntu Feisty. Up until a few days ago, it was working perfectly. Now, whenever I use beryl instead of the gnome window manager, the top part of all windows (with the minimize, maximize, close icons) vanishes. Keybindings also don't work. The workspaces/viewports don't work either. I have the diamond thing up in the top right of my screen (by the clock and update notifier). From there, I am able to access various beryl settings (including emerald). I have tried reinstalling beryl, but I can't get it working. Any help would be greatly appreciated.

---

### Post by Paerez on 2007-02-02
The recent versions of beryl have been messing things up. They are almost at a 2.0 release (about 2 weeks) and the last couple have been buggy.

Open up Synaptic, find the beryl packages and force their version to 1.4 instead of 1.999. Then log out and back in again.

Then in a couple weeks, go back and update them.

---

### Post by nhandler on 2007-02-02
That got beryl working. But emerald (the theme manager) won't work. Is there any way to fix that?

---

### Post by Paerez on 2007-02-02
do the same thing to emerald.

---

### Post by nhandler on 2007-02-03
> **Paerez said:**
> do the same thing to emerald.

It won't let me. I have the newest emerald installed. When I force the version of emerald to 1.4, it removes libemeraldengine0 and emerald. It won't let me downgrade them. Can I do this from a terminal?

---

### Post by ronmarley1 on 2007-02-03
> **Cheater said:**
> I have Beryl installed on Ubuntu Feisty. Up until a few days ago, it was working perfectly. Now, whenever I use beryl instead of the gnome window manager, the top part of all windows (with the minimize, maximize, close icons) vanishes. Keybindings also don't work. The workspaces/viewports don't work either. I have the diamond thing up in the top right of my screen (by the clock and update notifier). From there, I am able to access various beryl settings (including emerald). I have tried reinstalling beryl, but I can't get it working. Any help would be greatly appreciated.
I had the same issue and removed beryl and beryl-core and then reinstalled both and all was fine.  You mention that you reinstalled, but you did not mention that you uninstalled first.  Try and and see if that works,  The Beryl forums may be a good spot to look also, [http://www.beryl-project.org/](http://www.beryl-project.org/).  Good luck!

---

### Post by nhandler on 2007-02-03
I simply removed beryl-plugins-extra and then did sudo-apt-get update sudo apt-get upgrade to upgrade my version of beryl again.

From the looks of the beryl forum, the 1.9 version (not sure on the exact number) didn't work for a lot of people. Check out the beryl forum for other solutions.

---

### Post by bigjoe4265 on 2007-02-03
For those having issues with the window decorator (missing) with the latest Beryl, I added the follwowing to the module section and restarted X and presto!

btw I have an Nvidia 7600GT card



```
Load "dri"
```

Bigjoe

---

