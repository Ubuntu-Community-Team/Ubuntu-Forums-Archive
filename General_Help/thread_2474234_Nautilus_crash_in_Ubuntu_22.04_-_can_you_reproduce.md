---
title: "Nautilus crash in Ubuntu 22.04 - can you reproduce?"
date: 2022-04-24
forum: General Help
---

### Post by Seb71 on 2022-04-24
Ubuntu 22.04

Open at least one instance of Nautilus ("Files").

Now try to open a second instance, using right-click on the Gnome Shell Dock (Dash to Dock or whatever is the default in Ubuntu 22.04) and selecting one of the quicklinks (such as "Documents", "Downloads", "Music", etc.) - so not "New Window" (this does not crash it).

In my case, Nautilus always crashes when I do this.

If Nautilus is not already open, I can start it by right-click on its icon on the Gnome Dock and selecting one of the quicklinks, without issues.

---

### Post by trogdor422 on 2022-04-24
I am experiencing the same issue.

---

### Post by Dennis N on 2022-04-25
It may not entirely be a Files (a.k.a. Nautilus) problem, since I can open multiple windows for the locations (some are bookmarks) on the Quick Link menu with Plank as the dock.

---

### Post by Seb71 on 2022-04-25
Yeah. Launchpad search is not working very well for me.

It appears that this bug is present since at least 21.04.

---

### Post by Seb71 on 2022-04-25
As mentioned in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1934579"), it only happens when using Wayland.

I just tested by switching to Xorg and in that case Nautilus does not crash when repeating those steps.

---

### Post by vanadium on 2022-04-25
@seb71: indeed, that will be it. Nice find!

---

### Post by deejayvit on 2022-04-26
I've just upgraded Ubuntu to 22.04 and noticed the same issue.
I'm forced to right click, select "new window" and click on the bookmarked link

---

### Post by Dennis N on 2022-04-26
Tip:
An alternative to the quick list is to use the "Places Status Indicator" gnome-shell extension, which allows one-click opening in a new window of any bookmark or standard home folder location (like Pictures). But, I don't know how it works with Wayland.

---

### Post by Briga on 2022-10-31
Apparently it is a bug that affect Nautilus only on Wayland. 

Easy solution: try to run it with -q. Open a terminal:
```
nautilus -q
``` 
seems to work (don't ask me why, -q is quit!)
Other solution: switch to X11. 

I went for the easy :D

---

