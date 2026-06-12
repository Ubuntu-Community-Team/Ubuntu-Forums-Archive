---
title: "Disabling screen locking when switching users?"
date: 2008-01-19
forum: General Help
---

### Post by afoglia on 2008-01-19
I've recently set up an old computer with Ubuntu Gutsy for my family as a temporary replacement for their recently deceased Windows box.  Since they're not use to such "wacky" things as passwords, I've disabled the passwords for logging in via gdm.  But since they never log out, when they switch back to their accounts with the fast-user switching, Ubuntu asks for their password.

I'm pretty certain what's happening is that the screen is somehow getting locked.

It's not getting locked by the screensaver.  I've unchecked the lock feature in the screensaver configuration, and verified that /apps/gnome-power-manager/lock_on_blank_screen and /apps/gnome-power-manager/lock_use_screensaver_settings are unchecked in gconf-editor.

Is there some other option that's set by default to lock the screen?

---

### Post by diaa on 2008-01-26
may be /apps/gnome-screensaver/lock_enabled too ?

---

