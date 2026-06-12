---
title: "Disable XGL for a single user"
date: 2007-10-22
forum: General Help
---

### Post by neko18 on 2007-10-22
Is it possible to disable XGL for a single user? It's taking about 5% of the CPU at all times. I looked in System>Preferences>Sessions but there was no mention of it there. I can't just uninstall XGL because the rest of my family likes the visual effects (which require XGL on my computer).

Thanks

---

### Post by pointone on 2007-10-22
This should work:

```
touch $HOME/.config/xserver-xgl/disable
```

---

### Post by neko18 on 2007-10-24
Thanks

---

### Post by AleTeck on 2008-03-25
Sorry, I'm a beginner. Can you explain me better please?
Thanks

---

### Post by misterhead on 2008-03-25
login to the profile you want to disable "glx" in

click places and select HOME.

Click the "view" tab and select "show hidden files" you will now see a folder called ".config". open it...

"right click" in the open window and selcet "create folder" 

right click and rename that folder "xserver-xgl"

open that folder and right click in it and select "create document" and then "empty file"

Right click that file and rename it "disable"

THAT's IT!

xserver-xgl will no longer start when that profile start's.

Undo it?... Delete the folder and file. 

Good luck.

---

### Post by AleTeck on 2008-03-28
ok, but if I would like make a special session without xgl ( i'll use it with battery).. how can i do?

---

### Post by misterhead on 2008-03-28
not sure about different sessions, but if the end result is "compiz" vs. "no compiz" at login. This might work for you.

[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

---

