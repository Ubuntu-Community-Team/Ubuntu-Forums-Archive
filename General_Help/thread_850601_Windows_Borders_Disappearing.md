---
title: "Windows Borders Disappearing"
date: 2008-07-05
forum: General Help
---

### Post by Aphelion02 on 2008-07-05
I realize this might belong in the Desktop customization and effects subforum, but since I'm not sure this is related to my other problem [here]("http://ubuntuforums.org/showthread.php?t=850597") I have put this in the main forum.

For the last two restarts, my windows borders have disappeared on all my windows. I can't resize or move anything. Attached is a screenshot of my system.

If anyone can be off help, it would be awesome.

---

### Post by theshadowwithanmp5n on 2008-07-05
this happened to me.
but i remeber it got fixed at sometime around the first time i updated.

maybe it could be that, but i don't know

---

### Post by raja on 2008-07-05
Looks like the window manager has crashed. Are you running gnome or KDE and is compiz running?

---

### Post by Aphelion02 on 2008-07-05
I am running gnome, and while I have the compiz manager installed, I'm not certain if it is actually running. Also, the problem fixes itself if I just go to change desktop background and toggle between and no desktop effects and normal desktop effects. I just don't want to have to do that everytime I start up.

---

### Post by linfidel on 2008-07-05
> **Aphelion02 said:**
> I am running gnome, and while I have the compiz manager installed, I'm not certain if it is actually running. Also, the problem fixes itself if I just go to change desktop background and toggle between and no desktop effects and normal desktop effects. I just don't want to have to do that everytime I start up.Next time it's working, try going to the "System", "Preferences", "Sessions" menu, and in the "Session Options" tab, press the button to "Remember Currently Running Application".

To get the borders back, you can probably type, from a terminal, "compiz --replace" if you're running compiz desktop effects, which it sounds like you are.

---

### Post by Aphelion02 on 2008-07-05
Thanks a lot! I checked under system preferences and it turns out that I am indeed running compiz, but thats not under one of my startup programs. How do I ensure that Ubuntu starts up w/ compiz?

Edit: My question is exactly what should I type when trying to add compiz in the command line.

---

### Post by linfidel on 2008-07-05
> **Aphelion02 said:**
> Thanks a lot! I checked under system preferences and it turns out that I am indeed running compiz, but thats not under one of my startup programs. How do I ensure that Ubuntu starts up w/ compiz?

Edit: My question is exactly what should I type when trying to add compiz in the command line.
I don't have compiz listed either.  But if you have advanced desktop effects enabled, it will be running.  But the command "compiz --replace" will run it, replacing whatever other one might be running.  

Compiz _**is**_ the desktop effects manager.

---

