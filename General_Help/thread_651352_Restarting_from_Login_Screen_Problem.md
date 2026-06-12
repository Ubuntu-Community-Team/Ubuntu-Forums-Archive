---
title: "Restarting from Login Screen Problem"
date: 2007-12-27
forum: General Help
---

### Post by Anthony M on 2007-12-27
When I am at the login screen and go to the restart/shutdown dialog button, if I choose Restart I am taken to a second login screen with a different theme where I  then have to choose Restart  again from that login screen before the computer actually restarts.

The first login screen is the default brown Ubuntu, the second is blue with flowers or something.

If I choose Restart from the normal GNOME panel, all is fine, it only happens if I log out then restart...

How do I get rid of this second login screen?



Thanks!

---

### Post by p_quarles on 2007-12-27
Sounds like you have both GDM and KDM (the display managers for Gnome and KDE) running simultaneously. That's not something I've seen before, to tell you the truth.

In any case, try running this command:
```
sudo dpkg-reconfigure gdm
```
This should bring up a dialogue that allows you to choose which of the two you want as your default display manager. 

That said, I can't be certain this will work, since this sounds like an unusual situation.

---

### Post by Anthony M on 2007-12-27
> **p_quarles said:**
> Sounds like you have both GDM and KDM (the display managers for Gnome and KDE) running simultaneously. That's not something I've seen before, to tell you the truth.

In any case, try running this command:
```
sudo dpkg-reconfigure gdm
```
This should bring up a dialogue that allows you to choose which of the two you want as your default display manager. 

That said, I can't be certain this will work, since this sounds like an unusual situation.

I just tried this and it made no difference. Also this was a fresh Gutsy install. KDE was never installed.

The problem is that after I choose Restart or Shutdown from the login screen, it attempts to find the "Circles" login theme even though I have "Ubuntu" theme chosen...

---

### Post by p_quarles on 2007-12-27
Okay, so somehow the default KDM login screen got onto your system. That's kind of strange. 

Anyway, try running this:
```
dpkg --get-selections kdm
```
If it indicates that the state of this package is "install," then that would seem to be part of the problem. Otherwise, the problem would have to be something else entirely.

---

