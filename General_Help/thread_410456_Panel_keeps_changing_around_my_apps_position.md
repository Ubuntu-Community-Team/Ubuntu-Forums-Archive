---
title: "Panel keeps changing around my apps position"
date: 2007-04-15
forum: General Help
---

### Post by Rutabega on 2007-04-15
Hi everyone. I need some help regarding the panel. Every time I log-in, my unexpanded panel completely changes the icons positions every time.  Do I need to save the session for the icons to stay put? also I would like how I can lock the panels in unexpanded mode, I currently want three panels, yet the smaller one keeps changing position every time I log-in. Ideally this is what I want the configuration to be like *all the time* :KS  

[[IMG]http://img410.imageshack.us/img410/2430/screenshotqz5.th.png[/IMG]](http://img410.imageshack.us/my.php?image=screenshotqz5.png)

---

### Post by orb9220 on 2007-04-15
You need to right click each icon and select lock  to panel.

---

### Post by Rutabega on 2007-04-16
The icons are already locked to the panel. Yet they still move around the panel upon log-in/start-up/

---

### Post by kvonb on 2007-04-16
Yeah, they'll do that! :S

I find if I lock them in position and log in/out a few times they stay, but every now and then they will shuffle!

There are quite a few "features" of the Gnome panel that seem to have a mind of their own!

---

### Post by Rutabega on 2007-04-16
So it's a rather standard occurrence then?, I hope this will be fixed in the future :(

---

### Post by kvonb on 2007-04-16
Unfortunately it's a Gnome problem which means that it is not an Ubuntu problem and has to be dealt with by the Gnome desktop project.

From my experience they aren't the fastest or keenest at fixing "features" (did that sound sarcastic? :D ), so you might be in for a bit of a wait.

However, Feisty is due out in a few days so you can always download the CD and give it a try.

I'm using Feisty and I can't recall having that problem yet.

---

### Post by anaconda on 2007-04-16
> **Rutabega said:**
> So it's a rather standard occurrence then?, I hope this will be fixed in the future :(

It is possible to lock them to their places using gconf-editor.. however even this can have some problems. 

I played once some game, which changed the screen resolution and when I exited the game my lower panel was on the middle of the screen and because I had locked the panels from gconf-editor I couldn't move it back. Took me hours to figure that I had to re-enable modifying panels before I could move it..

---

### Post by srt4play on 2007-04-16
For the rearranging icons, try locking only your menu, clock and power button on the top one.

Lock only your show desktop, window list, and trash on the bottom one.

And don't lock any on your launcher bar. 

Try that.

---

### Post by Rutabega on 2007-04-16
The icons on the panel are okay when placed on the side, rather peculiar, yet the application panel completely shuffles when not expanded. I'll try your suggestion srt4play of unlocking the apps.

---

### Post by lotacus on 2007-04-16
heh. This is a common occurance. This happens to me when I change resolutions. I suspect this happens because the people behind the project use absolute values in determining the position of the icons relitive to the screen.

---

