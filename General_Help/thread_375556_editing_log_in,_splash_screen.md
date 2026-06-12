---
title: "editing log in, splash screen"
date: 2007-03-03
forum: General Help
---

### Post by valke on 2007-03-03
i have successfully installed a new splash screen, very nice. now i would like to somehow edit the "splash screen" (not sure what to call it) the screen that greets you after a successful log-in. i have edited my login window, but i am not sure what to do next. please and thank you.

---

### Post by valke on 2007-03-04
bump

---

### Post by yabbadabbadont on 2007-03-04
If it is the one I think you are talking about, it is in /usr/share/pixmaps/splash.

---

### Post by valke on 2007-03-04
ok but is there an applet associated or a preference settings thingy? so i can choose, i cant explain very well.

---

### Post by yabbadabbadont on 2007-03-04
No.  There is a setting in the gconf-editor for it, but it defaults to the symbolic link that you will find in that directory.  Just change the link to point to your own image to change which one is used.

---

### Post by valke on 2007-03-04
any recommendations for sites with other splashes? thank you that is what i was looking for.

---

### Post by yabbadabbadont on 2007-03-04
[http://www.gnome-look.org/index.php?xcontentmode=160](http://www.gnome-look.org/index.php?xcontentmode=160)

---

### Post by valke on 2007-03-04
thank you.

---

### Post by valke on 2007-03-04
ok, now that i have one how do i move it into the /usr/share/pixmaps/splash folder? i opened terminal, and cd /usr/share/pixmaps/splash.

```
sudo aptitude install gnome-splashscreen-manager
```

there is a manager! yay!

---

