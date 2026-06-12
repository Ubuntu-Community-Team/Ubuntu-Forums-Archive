---
title: "Screen sharing/recording no longer works as of 17.10 upgrade"
date: 2017-11-12
forum: General Help
---

### Post by r.whitney on 2017-11-12
After upgrading to 17.10 all of my screen recording/sharing apps have stopped working. I can no longer use Teamviewer, Discord screensharing, OBS screen recording, and when I press Ctrl+Shift+Alt+R my computer hard locks!
I have tried on upgrade from 17.04 and a fresh install of 17.10 on my laptop.

---

### Post by Perfect Storm on 2017-11-12
At the login screen, click the cog button. Change the login to xorg instead. It might be the applications you are using are not compatible with wayland.

---

### Post by r.whitney on 2017-11-12
That works! You're amazing thanks! :)
Now I wonder if/when there will be a fix for any of those programs.

---

### Post by Perfect Storm on 2017-11-12
If want to be sure an email to the owners of these apps and asking them about wayland support is the best way you can do. :)

---

### Post by r.whitney on 2017-11-12
I will do, thanks again. :)

---

### Post by r.whitney on 2017-11-12
It may also be worth noting that when in Wayland `xset -led 3` does not turn on the back light on my keyboard. This is usually turned on under Windows by pressing the Screen Lock button.

---

