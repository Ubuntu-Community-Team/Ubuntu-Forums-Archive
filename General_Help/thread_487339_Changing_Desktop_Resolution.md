---
title: "Changing Desktop Resolution"
date: 2007-06-28
forum: General Help
---

### Post by hawk16 on 2007-06-28
I recently downloaded and installed xubuntu on a P3 1Ghz laptop. The screensize is wierd so it uses a different resolution then the default one, however the default one is glitched out and I cannot see the menu bar to change it. How would i go about changing my resolution without access to this? All I can see is like the desktop with a folder on it. And if I right click, its just desktop settings not actual resolution settings.

---

### Post by hawk16 on 2007-06-29
It's also 7.04 and im stuck on the login screen, I cannot see the box to login.

---

### Post by hawk16 on 2007-06-29
It's also like flickering blue bars going up and down that is blocking the login screen.

---

### Post by hawk16 on 2007-06-29
I'm also a complete newb and I need step by step directions.

---

### Post by CocoAUS on 2007-06-29
Does the livecd work ok, or is the resolution screwed up on there, too?

---

### Post by Qu4k3R on 2007-06-29
You might need to change your xorg.conf file.
I think there are some tutorials over here.

NOTE: This might get you problems. Read the papers about xorg.conf first !!

How do I change the resolution (force):
In a terminal:
> 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo <text_editor> /etc/X11/xorg.conf

Then I just added the resolution I needed.
Then just oppen your resolution configuration tool (system>preferences) and change it.

Hope it works ;)

PS: There are more topics related to xorg.conf and tutorials about it and how to change the resolution. I would search about them.

If it works for me, it should work for you ;)

---

