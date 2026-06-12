---
title: "Issues logging off when multiple users logged into system"
date: 2007-11-26
forum: General Help
---

### Post by Lord_Dicranius on 2007-11-26
As the subject states, I'm having issues logging out of accounts when more than one user is logged into the system.  I share a laptop with my wife, we use separate accounts (she doesn't like my wallpaper hehe).  So we'll use the user switcher to switch back and forth between our accounts.  But whenever we try to log off one of the accounts, it'll go to a blank black screen, then just sit there and do nothing.  I can move the mouse, but none of the keys will respond.  I've let it sit for 30 mins, and came back, still a blank black screen.  Only thing I've found that'll work is pushing/holding the power button to shut down, then start it back up.  But this is an issue as when one person tries to logout and we have to power it down, the other person loses out on everything they still had open.

Anybody else have this issue?  Or should I file a bug? :confused:

---

### Post by geirha on 2007-11-26
It certainly qualifies as a bug, so filing a bug report would be a good idea. When this happens though, could your try hitting CTRL+ALT+F7, CTRL+ALT+F8, try with all the top F-keys above F7 really, it should switch between the different X-displays. F1-F6 are console displays. Another key combination is CTRL+ALT+Backspace. This key-combo will kill the X-server in the screen you're on, and should bring you back to the login-screen.

---

### Post by petersjm on 2007-11-26
> **geirha said:**
> It certainly qualifies as a bug, so filing a bug report would be a good idea. When this happens though, could your try hitting CTRL+ALT+F7, CTRL+ALT+F8, try with all the top F-keys above F7 really, it should switch between the different X-displays. F1-F6 are console displays. Another key combination is CTRL+ALT+Backspace. This key-combo will kill the X-server in the screen you're on, and should bring you back to the login-screen.

This is good advice. I had this issue myself a couple of times. It seemed (though I know very little about it, really) that when one user logged out, the screen failed to return to the other user's x-display. Hitting CTRL+ALT+F7 (the first X-display screen) brought it back to the first user's account.

EDIT: Also, do you lock-and-switch users or just switch them? Locking them *might* have an effect on this, but I can't say for certain.

---

### Post by Lord_Dicranius on 2007-11-26
Thanks for the tips guys.  I've tried CTRL+ALT+Backspace, and that didn't do anything.  I'll give the CTRL+ALT+F# keys when I get home and let you know how it goes.

As for switching, it occurs whenever I use either the user switcher app on the panel, or hitting the quit button and select "switch user".

Be back with results later tonight :-)

---

