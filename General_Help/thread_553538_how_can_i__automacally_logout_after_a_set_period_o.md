---
title: "how can i  automacally logout after a set period of time?"
date: 2007-09-17
forum: General Help
---

### Post by Darth_tater on 2007-09-17
i have one account automatically login and a few programs for that user (that require they be started in a gui) start.  but this is relatively insecure, as this box is supposed to be headless.

is there any way that i can make my profile automatically login in (already figured this part out)... but then wait, say, 20 or so seconds before autolocking the screen?


actually, if i immediately login and then lock the screen will the rest of my 'start at login' apps load even tho the command to lock the screen has been issued? if so, how can i get the screen to immediately lock after i have logged in?

---

### Post by aysiu on 2007-09-18
Add this command to System > Preferences > Sessions > Startup ```
gnome-screensaver-command --lock
```

---

