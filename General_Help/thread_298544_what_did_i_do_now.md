---
title: "what did i do now?"
date: 2006-11-12
forum: General Help
---

### Post by pentium on 2006-11-12
After spending the last hour fighting for control over the system because a simple gif thumbnail overlaoded the system, I finally got it under control and shut the system down.
But when I logged back in my desktop was gone! all programs in the menu's were still good and file browser said the desktop was populated. Another strange thing is that I can right click on everything but the desktop and get the right click menu. Somehow the system forgot that there is a desktop and it won't even allow for dragging icons back to the desktop.

What did I do?

---

### Post by bruenig on 2006-11-12
> **pentium said:**
> After spending the last hour fighting for control over the system because a simple gif thumbnail overlaoded the system, I finally got it under control and shut the system down.
But when I logged back in my desktop was gone! all programs in the menu's were still good and file browser said the desktop was populated. Another strange thing is that I can right click on everything but the desktop and get the right click menu. Somehow the system forgot that there is a desktop and it won't even allow for dragging icons back to the desktop.

What did I do?

This happened to me before. I rebooted and it started working again.

---

### Post by strabes on 2006-11-12
try killall gnome-panel ?? I have no idea. Check in gconf-editor in apps/nautilus/preferences if show_desktop is checked. If not then check it and I think that should fix your problem.

---

### Post by pentium on 2006-11-12
uh oh.
It's checked. and still no desktop.

---

### Post by pentium on 2006-11-12
okay, I think we are getting somewhere.
I sifted over the logs and apparently while I was having my overload problems with thumbnails nautilus was being killed over and over again to free memory.
I double checked to see what loads when I login and I don't think nautilus is loading at all!
Somehow the system keeps forgetting to load nautilus.

---

### Post by pentium on 2006-11-12
FIXED!
It seems that nautilus WAS NOT running at login.
Running it from terminal brought it on. Now I just gotta remember again how you make it run at login.

thanks for the tips. I probably would of never looked through the logs.

---

