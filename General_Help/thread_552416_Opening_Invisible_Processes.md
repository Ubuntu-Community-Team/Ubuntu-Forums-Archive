---
title: "Opening Invisible Processes?"
date: 2007-09-16
forum: General Help
---

### Post by greg73654 on 2007-09-16
OK, here's my problem, I have deluge-torrent (v0.5.5 in case your wondering...) running, it had an option to allow it to go to the system tray, and I also set an option to start in the system tray... Now my problem is when I try to restart it and look at the gui, it won't show it in the system tray and the only way I can see it is in the System Manager... How do I open it back up to change the option?

---

### Post by peabody on 2007-09-16
Sounds application specific.  I haven't heard of deluge-torrent before.  My guess is that you would have to edit the configuration information yourself for the app.  It will be held in two possible places 1) a hidden folder in your user folder or 2) if it's a gnome app, it's settings might be held in gconf, in which case you'll have to open up the gconf editor and find the folder for its settings in there.

---

### Post by greg73654 on 2007-09-16
Where would the gconf be?

---

### Post by peabody on 2007-09-16
you'd use the gconf-editor command from a terminal to launch it.

if the app in question isn't a gnome-app (many gui programs aren't gnome apps) it's config info more than likely will not be there.

---

### Post by greg73654 on 2007-09-16
So is there anyway I can put the configuration back to defaults on an application?

---

### Post by peabody on 2007-09-17
> **greg73654 said:**
> So is there anyway I can put the configuration back to defaults on an application?

As stated before, that's application specific.  I am completely unfamiliar with deluge-torrent.  You'll have to try google.

---

