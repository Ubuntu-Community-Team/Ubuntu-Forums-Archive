---
title: "help, to taskbars!!"
date: 2007-01-27
forum: General Help
---

### Post by StOnE LiBeRaTiOn on 2007-01-27
I was messing around, chaning the color of my task bar, and then I decided to add a picture.... Well that pictures reselution was huuge, and apparently, my computer doesn't handle large images too well for the taskbar... So, now my taskbars are all gone, and  I have no idea how to get them back.  Is there a way I can go into terminal or the root file system and reset my taskbars, or remove the image I added...
please help
thanks!!

---

### Post by dexter on 2007-01-27
Try alt+f2, in which you can execute commands. You can restart the panels using "killall gnome-panel".

---

### Post by StOnE LiBeRaTiOn on 2007-01-27
alt+f2 didn't do anything?

---

### Post by dexter on 2007-01-27
In that case hit ctrl+alt+f1, which should give you a terminal, log in and type "killall gnome-panel", to go back to graphic mode hit ctrl+alt+f7

---

### Post by StOnE LiBeRaTiOn on 2007-01-27
gnome-panel: no process killed

no luck... its probaly becuase im using beryl....

---

### Post by StOnE LiBeRaTiOn on 2007-01-27
any other ideas?

---

### Post by StOnE LiBeRaTiOn on 2007-01-27
bump

---

### Post by Ramses de Norre on 2007-01-27
```
gconf-editor /apps/panel/toplevels
```
search the panel you've set the image on, expand it and in the background directory set the "image" option to an empty string.

---

### Post by StOnE LiBeRaTiOn on 2007-01-27
I probaly have to enter that code within the gui right... How do i open up a terminal without having my taskbar, and within the gui?

---

### Post by StOnE LiBeRaTiOn on 2007-01-28
good news... fixed it... I made a thing on the desktop so i could start a terminal within the gui, then i did gconf-editor /apps/panel/toplevels  and followed the instructions ramses gave.... thanks guys

---

