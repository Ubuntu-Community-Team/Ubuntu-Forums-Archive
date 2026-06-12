---
title: "applying xgl themes"
date: 2006-08-25
forum: General Help
---

### Post by janthan on 2006-08-25
installed and works but how to i apply themes?
ive been to cgwd themer which allows me to edit themes but not apply them ](*,) 
please put me out of my misery, its probobly pretty obvious but after an hour of searching on the net and through the configuration i cant find it ](*,)

---

### Post by -DarkMind- on 2006-08-26
same problem here:|

---

### Post by cptjaben on 2006-08-26
I had the same problem as well, after searching for a way in install them from cgwd themer for 30minutes+ I gave up.

---

### Post by h00s on 2006-08-26
Do you have cgwd or gnome-window-decorator running?
Your compiz run script should be like this (cgwd must be running instead of gnome-window-decorator):
```
#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &
compiz --replace gconf &
```

---

### Post by -DarkMind- on 2006-08-26
> **h00s said:**
> Do you have cgwd or gnome-window-decorator running?
Your compiz run script should be like this (cgwd must be running instead of gnome-window-decorator):
```
#!/bin/sh 
killall gnome-window-decorator 
wait

cgwd &
compiz --replace gconf &
```

thanks

change gnome-window-decorator with cgwd works for me :D

---

### Post by h00s on 2006-08-26
Great! :mrgreen:

Cheers

---

### Post by DrPestilence on 2006-09-02
alas! that has not done it for me, any other sugestions?

---

### Post by Moisteh on 2006-10-07
I'm assuming my issue falls under this one.

I need the supposed "gcompizthemer" to get THIS working:

[http://www.gnome-look.org/content/show.php?content=44364](http://www.gnome-look.org/content/show.php?content=44364)


but i can't find it anywhere...

help?

im emulating the mac-look on linux...

AND ALSO:

i have a .tar of mac-cursors...how do i get them running?

thanks

---

