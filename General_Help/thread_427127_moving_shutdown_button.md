---
title: "moving shutdown button"
date: 2007-04-29
forum: General Help
---

### Post by cisforcojo on 2007-04-29
Hey all,

I've accidentally moved the shutdown in the top panel in GNOME. How can I move it back to the far right? It's not even in the most right "box" anymore. Just 'Move'ing the button doesn't work.

Thanks!

---

### Post by eriK-B on 2007-04-29
maybe this works:

Right click on the panel on which the button should be and choose "Add to panel..."
in the Desktop & Windows section there is a shutdown button.

Drag & Drop that button to the place on the right panel where you would like to have it.

Than right click on the old button(the one you accidentally moved) and choose "Remove from panel"

that should do it :)

---

### Post by mcduck on 2007-04-29
Just drag it where you want with middle mouse button or by right-clicking and selecting 'move'. If there are some other applets on the way and you can't drag the applet past them then you need to right-click those applets and make sure 'Lock to Panel' is not selected..

---

### Post by cisforcojo on 2007-04-29
Yeah got it. I was trying the 'Move' option but it was just being finicky. There is a divide between the far right and the middle part of the panel and for some reason I couldn't move back across the divide. I moved it to the left but couldn't go back right. I turned off all "Lock to Panel"s too. I ended up just readding it as far right as possible and then moving it.

Thanks for all your help!

Problem resolved.

---

### Post by cisforcojo on 2007-04-30
I take it back it's not fixed. My computer crashed before reboot so now a bunch of icons are in the middle of the top GNOME panel. Ugh. How can I move icons from the middle to the "notification area" (the far right section of the top panel)? I can't get them past the divide. I've disabled all lock to panel options but I got nothin.

---

### Post by eriK-B on 2007-04-30
try the way i described above, 
basically that means just adding a new one on the right spot and removing the old one

---

### Post by jputman01 on 2007-04-30
or just remove the divider, then move the icons, then readd the divider

---

### Post by zvacet on 2007-04-30
```
gconf-editor
```
[B]
apps>panel>applets>notification_area_screen0>unlock[/B]

After this go to the panel and you will be able to move icons left or right as far as you want.Once you do it as you like it back to the apps>panel>pplets>notifisation_area_screen0 and chek it.

---

### Post by cisforcojo on 2007-04-30
You, sir, are a filthy genius.

I never would've gotten that by myself. Thank you so much!

---

### Post by ps_kishore on 2008-04-07
I had the same issue, but this didnt help, here is the screen shot, After making the notification area to unlock, i still couldnt dragthe shutdown button to the right end corner. Take look at the screenshots.

---

