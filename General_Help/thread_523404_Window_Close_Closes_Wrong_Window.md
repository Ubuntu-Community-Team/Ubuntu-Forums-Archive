---
title: "Window Close Closes Wrong Window"
date: 2007-08-11
forum: General Help
---

### Post by gregladen on 2007-08-11
Here is what happens on my computer, running Feisty Fawn, Gnome:

A window is open and mazimized.  I open and mazimize a second window.  I put my mouse over the "X" in the upper right hand corner of the window that is now on top and click it.

Instead of this mazimized window closing, the window BEHIND it closes!  The "top" window remains open.

This does not always happen.  I'm pretty sure my computer works normally for a while, then this starts to happen, then it happens maybe 8 out of 10 times thereafter.

It does not seem to matter which software is running in any of the windows.

I am running UBUNTU Feisty Fawn version 7.04, with Compiz and restricted drivers on.  

If I open the two  windows as described above, then go to another desktop workspace, open and close a window there, then go back to then try to close the top of the current window, this behavior does not seem to ever happen.  

Has anyone heard of anything like this?  Is there other information I should provide?

I also have that bug discussed elsewhere where my computer freezes now and then, so I can move the mouse but clicking on things or using keyboard shortcuts for most things does not work.  In my case, the computer does not ever seem to unfreeze, but I have not necessarily waited long enough.  I'm mentioning this in case it is related.  

Any help or suggestions would be much appreciated!  In the mean time I close windows by going to the task bar and right clicking and choosing close.

---

### Post by Happy_Man on 2007-08-11
That is a compiz problem. It will be torture to try and change every setting to see what is the problem, so I suggest deleting the .compizconfig folder in your /home. That should wipe all user settings, so your problem will go away. If it doesn't, post back.

---

