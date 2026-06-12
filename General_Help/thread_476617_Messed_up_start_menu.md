---
title: "Messed up start menu"
date: 2007-06-17
forum: General Help
---

### Post by pickarooney on 2007-06-17
While trying to edit the properties of the K-menu (for some reason it displayed a Find Files icon instead of the K symbol) I accidentally deleted it. How do I go about getting it back?

On an unrelated subject, what's the best way to get a program to start with KDE (GMail notifier in this case) - in my .bashrc script or somewhere else? KTorrent currently starts whenever I log in although it's not in my .bashrc file

---

### Post by Old *ix Geek on 2007-06-17
> **pickarooney said:**
> While trying to edit the properties of the K-menu (for some reason it displayed a Find Files icon instead of the K symbol) I accidentally deleted it. How do I go about getting it back?
. Right-click anywhere on the panel [where KMenu used to be].
. Select "Add Applet to Panel"
. Find KMenu in the list; highlight it
. Select "Add to panel"

---

### Post by pickarooney on 2007-06-17
D'oh! Cheers :)
The icon is still displaying wrongly though, wonder why that is?

---

### Post by cookies on 2007-06-17
> **pickarooney said:**
> D'oh! Cheers :)
The icon is still displaying wrongly though, wonder why that is?

The icon set you are using must have an icon called kmenu.png that looks like a find files program. 

As for startup, just copy/link, the executable file to

~/.kde/Autostart

---

### Post by pickarooney on 2007-06-17
> **cookies said:**
> The icon set you are using must have an icon called kmenu.png that looks like a find files program. 

As for startup, just copy/link, the executable file to

~/.kde/Autostart

Nope. I checked every sized icon in the theme and they're all correct. The tooltip for the start button shows the correct icon too. Weird.
[edit]Ahh, there were icons in /actions sub-directories and these were messed up. Mystery solved.

Thanks for the startup tip.

---

