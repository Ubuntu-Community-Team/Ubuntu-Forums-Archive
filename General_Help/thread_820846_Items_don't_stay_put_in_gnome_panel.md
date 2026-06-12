---
title: "Items don't stay put in gnome panel"
date: 2008-06-06
forum: General Help
---

### Post by frogitts on 2008-06-06
Often, especially after running a full-screen game, my items get moved around on the gnome panel, especially the window button I have in the middle of my panel. This is very annoying, especially because they're locked, so that means I have to move them back from the locked position, reposition them, and lock them again. Is there anyway to make the "Lock" option ACTUALLY lock the item?

---

### Post by frogitts on 2008-06-11
It's still happening to me a lot, and it's really annoying. I've tried locking the whole panel from changes via gconf, to no avail. Does anyone else even have this problem, or am I the only one?

I would imagine that conflicting settings in gconf (apps > panel) have something to do with it. Does anyone have any ideas in this direction?

---

### Post by Het Irv on 2008-06-11
Does everything move left?

It may be that when you run the game, it uses a small resolution that your desktop.  When the game changes the resoultion it moves the Icons. Try changeing the resoultion on the game, and run the game twice, since the first time it will move the icons again.

---

### Post by frogitts on 2008-06-14
Actually, the most common thing to happen is for my one applet in the very middle of the panel to align itself with the applets on the right hand side - that is, it moves over to the side until it runs into an applet, and then stays there. 

Other than that, my right side applets will switch their order - my power button will get stuck in the middle of all of them, the clock will move to the leftmost position, other applets will switch spots.

Interestingly enough, this never happens on the left hand side, which may be why the full-screen apps seem to have something to do with it.

---

### Post by groovomata on 2008-06-17
I have a similar problem with my gnome panel that happens when I log out and log in again, or if I reboot my laptop. The Icon order changes. The window Selector Icon and the Workspace Switcher Icon migrate to the right, past several other icons, to the extreme right side of my screen. Which I don't like because I'm a nerdy kind of guy. 
Does anyone know of a fix?
Regards,
Erik.

---

### Post by DaymItzJack on 2008-06-18
I fixed this problem by going to System->Preferences->Sessions and hitting "Remember currently running applications" in the last tab. (Of course if you do this, make sure you're not running a bunch of programs)

---

### Post by vausey75 on 2008-09-12
Hi, I'm a newbie to Ubuntu running version 8.04 on a lenovo N200 laptop, Is there any way that I can lock my workspace switcher as everytime I move my finger on the mousepad it tries to swap workspaces, Very annoying and making me feel motion sick. Thanks, Stuart

---

### Post by schizostatic on 2008-09-12
lol I have the same issue, I have just gotten used to not placing my finger near the right side of the touch pad.

---

### Post by Het Irv on 2008-09-12
> **vausey75 said:**
> Hi, I'm a newbie to Ubuntu running version 8.04 on a lenovo N200 laptop, Is there any way that I can lock my workspace switcher as everytime I move my finger on the mousepad it tries to swap workspaces, Very annoying and making me feel motion sick. Thanks, Stuart
Are you using Compiz? If so you can go into the CCSM and disable the edge cube flip.  I usually use the keyboard shortcut (Ctrl + Alt + arrow key)

---

