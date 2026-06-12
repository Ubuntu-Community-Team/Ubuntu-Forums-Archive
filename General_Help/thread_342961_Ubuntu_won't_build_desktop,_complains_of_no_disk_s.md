---
title: "Ubuntu won't build desktop, complains of no disk space"
date: 2007-01-20
forum: General Help
---

### Post by Jack_O_Lantern on 2007-01-20
So out of the blue Ubuntu has decided to stop allowing me to log in using the GUI (Gnome).  It started after I had logged successfully into the GUI and was noticing that it wasn't allowing me to open anything from System>Preferences.  So, I restarted my machine and tried logging in again.  When this happened, the rectangular screen that shows the loading process of the desktop opens for about 2 seconds before closing.  Then, I am prompted with a window that says I have been logged out after only 10 seconds, and that this may be because of lack of disk space.  It then allows me to view a log file that only really says I have no fonts installed/configured.  It then proceeds to log me out back to the initial login screen.  

I have determined this must be a user-specific thing because I can log in using this user w/out the GUI (as a command-line terminal).  I can also log into the gui successfully using other users I've created.  Is there any way I can fix this user account?  I have tried deleting the uer's .gnome, .gnome2, .gnome2_private, .gconf, .gconfd, .metacity folders without any success.

Any suggestions?

---

### Post by dcstar on 2007-01-21
> **Jack_O_Lantern said:**
> So out of the blue Ubuntu has decided to stop allowing me to log in using the GUI (Gnome).  It started after I had logged successfully into the GUI and was noticing that it wasn't allowing me to open anything from System>Preferences.  So, I restarted my machine and tried logging in again.  When this happened, the rectangular screen that shows the loading process of the desktop opens for about 2 seconds before closing.  Then, I am prompted with a window that says I have been logged out after only 10 seconds, and that this may be because of lack of disk space.  It then allows me to view a log file that only really says I have no fonts installed/configured.  It then proceeds to log me out back to the initial login screen.  

I have determined this must be a user-specific thing because I can log in using this user w/out the GUI (as a command-line terminal).  I can also log into the gui successfully using other users I've created.  Is there any way I can fix this user account?  I have tried deleting the uer's .gnome, .gnome2, .gnome2_private, .gconf, .gconfd, .metacity folders without any success.

Any suggestions?

At a guess, possibly the Quota for this user is set far too low.

Remove the quota settings (or package) and see if things change.

---

