---
title: "Panel transparency issue"
date: 2008-06-19
forum: General Help
---

### Post by djmoore85 on 2008-06-19
Hey yall, quick question here. I have compiz running smooth finally, I installed cairo-dock and have it up and running, but ran into a snag. I have been trying to make my top GNOME panel transparent, due to I can't get the GNOME main menu attached to cairo-dock for easy access to my programs. I want it transparent so that there is just the "start" button in the top left corner of my screen and then the dock below. But when set to transparent, I am getting this weird shadow on the bottom edge of the GNOME panel, and want to get rid of it so as to have a "clean" wallpaper from top to bottom. Thansk in advance for any help.

---

### Post by Vadi on 2008-06-19
It's a compiz effect I think that gives it the shadow, but I forget the rule that you need to add to compiz to have it exclude the panel unfortunately.

---

### Post by Enlitend on 2008-06-19
Ok I just try this out.

CCSM-> Effects-> Winodw Decoration :

look for "Shadow windows" on the bottom and add this line so it look like this :

```
(any) & (class=Gnome-panel) & (type=DropdownMenu) 
```

that will get rid the panel's shadow but will preserve your main menu's shadow. 
it will get rid off the tooltip's shadow too if you don't mind that.
Hope that helps.

---

### Post by djmoore85 on 2008-06-20
Thanks man  appreciate it, worked like a charm. Looks much cleaner now. Tanks again!

---

### Post by Enlitend on 2008-06-20
Glad it works for you. :)

---

