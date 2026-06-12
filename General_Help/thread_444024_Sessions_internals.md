---
title: "Sessions internals"
date: 2007-05-15
forum: General Help
---

### Post by pferrel on 2007-05-15
I seem to have a startup order problem but have not been able to find where the startup order or programs are stored by gnome-session-properties.  Can someone point me to some docs on the gnome sessions?

My specific problem is a very slow startup after gnome loads.  Some of my UI widgets seem to wait on my wireless connection to be displayed or Beryl startup or some such.  Also Cairo-clock is hidden and has to be restarted.   

Anyway I'd like to understand the gnome auto startup architecture.

---

### Post by jmoorse on 2007-05-20
~/.config/autostart/ should be it

---

