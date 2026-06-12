---
title: "Upgrading Fluxbox crippled system"
date: 2007-10-15
forum: General Help
---

### Post by Kossilar on 2007-10-15
Hey all. 

I've been using Ubuntu all out now for a few months. I switched away from Gnome to the Fluxbox window manager. Its pretty tight, uber fast and customizable. 

Shortly after installing the new version of Fluxbox I downloaded a package of Fluxbox themes and unpacked them and in the middle of the operation, my box stopped responding. Or rather, programs stopped responding to input. That is, Nautilus doesn't accept mouse input anymore, although the buttons do light up when the mouse is over them I just can't click them. 

Every single program is like this and in fact, I can only open them using my tilda console, because the Fluxbox menus can't be clicked on either, even though I can bring them up as usual. 

I've already deleted the themes, although I doubt that a bunch of text files could cause this kind of catastrophe. 

No answers from the Fluxbox community so far. 

Any ideas what could be causing this?

---

### Post by yabbadabbadont on 2007-10-15
Try moving your ~/.fluxbox directory to a different name, like ~/.fluxbox-borked.  Then let startfluxbox create a new one for you.  (it is what is run when you choose a fluxbox session)  If that works, then you can start comparing the files in the two directories to try to figure out exactly what screwed everything up.

---

### Post by Kossilar on 2007-10-16
Do I need to run startfluxbox myself? I tried what you're suggesting but FB just kicked me back into Gnome when it saw there was no .fluxbox directory.

---

### Post by yabbadabbadont on 2007-10-16
If you are using the GDM graphical login manager, there should be a file /usr/share/xsessions/fluxbox.desktop that contains the line ```
Exec=/usr/bin/startfluxbox
```  If the Exec line does not call startfluxbox, but instead fluxbox, change it and try again.

---

