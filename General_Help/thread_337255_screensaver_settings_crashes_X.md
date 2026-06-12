---
title: "screensaver settings crashes X"
date: 2007-01-12
forum: General Help
---

### Post by J-Rod on 2007-01-12
I don't know how this came about, but I have a strange issue I am not sure how to sort out. If i try to access screensaver settings from System->Preferences->Screensaver I get an instant crash to the GDM logon screen. It also appears the system will crash when the screensaver activates after the default 10 minutes. I don't really *need* a screensaver, I'd be happy enough to know how to change the screensaver setting from terminal for now. Has anyone else run into this, or have a pointer as to where I can do more reading?

---

### Post by ivanmt42 on 2007-04-06
I'm having the same problem... any solutions?

---

### Post by the_ferkel on 2007-04-13
same here. no solution yet. :(

---

### Post by the_ferkel on 2007-04-13
Hey! I may have a solution:

Seems to be an OpenGL screensaver which crashes.
I just removed the package xscreensaver-gl and now i can access the screensaver contol panel again.

$ sudo apt-get --purge remove xscreensaver-gl

Since I don't really need screensavers with OpenGL it's fine for me.

---

### Post by woknblues1 on 2008-01-29
the solution given did not remove my screensaver, and I still get an instant crash. what did I do wrong? 7.10 AMD64...

---

### Post by robenroute on 2008-02-11
> **woknblues1 said:**
> the solution given did not remove my screensaver, and I still get an instant crash. what did I do wrong? 7.10 AMD64...

Same here: tried the proposed solution (removing OpenGL screensavers) to no avails.

Anyone out there with an answer to this annoying problem?

---

