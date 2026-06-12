---
title: "session assistance"
date: 2008-01-07
forum: General Help
---

### Post by Tristam Green on 2008-01-07
I have avant-window-navigator set to start up on session start.  However, it does not look correct, so I figured I'd allow it to sleep for 10 seconds then start the AWN program.  I set the command "sleep 10 && avant-window-navigator" in the options for AWN under "System>Preferences>Sessions", and now upon login GNOME will no longer start.

How would I recover from this?

---

### Post by Tristam Green on 2008-01-07
i think i figured it out.

referencing [this thread](http://ubuntuforums.org/showthread.php?t=358604),  i removed ~/.config/autostart/avant-window-navigator.desktop from the command-line and it appears all else is working peachy-keen.

score one for "looking it up yourself"!

---

