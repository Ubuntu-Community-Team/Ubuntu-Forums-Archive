---
title: "Crash to welcome screen on login"
date: 2007-04-10
forum: General Help
---

### Post by craz on 2007-04-10
A few days ago, my computer lost power while Ubuntu 6.10 edgy was running.  I came home later that day and turned my computer back on.  When I logged into my user account, the panels, desktop icons, and wallpaper all loaded.  Then it crashed to a black screen and returned to the welcome screen.  If I attempt to login again, it doesn't even start to load before crashing, and will not do so until I restart the computer.  There is no error message.  I cannot login to gnome-safe either because it crashes with an error message about not being able to load Gnome settings and not being able to run startup scripts.  I have already used CTRL-ALT-F1 to login and I re-installed the gnome panels and ubuntu-desktop and its dependencies and my account still will not work.  I CAN login to the root account by typing startx.  All my customizations are pretty much gone now and Ubuntu doesn't work.  I'd like it back!  If anyone can help I would appreciate it _greatly_.  Thanks a lot.

---

### Post by Smuve on 2007-04-10
I had a similar problem after an update a few days ago, there was a update to xorg.  My desktop would boot up just fine, but if I tried to run beryl or if my screensaver started, it would crash me back to the welcome screen.  From those two symptoms, I think it had something to do with GL. 

If you have anything in your start up script that uses GL after everything else starts up, that's probably why you don't get as far I did before the crash. 

To fix it, I had to reinstall my video drivers (nvidia).  If you're using the generics, do a 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by craz on 2007-04-10
Thank you so much!  I was nervous because I had already done what you mentioned, however when I re-installed my Nvidia driver like you suggested, it worked great and I am back on Ubuntu.  Thank you so much!

---

### Post by Smuve on 2007-04-10
No problem.  I was terribly confused when I came back to my terminal and it was at the login.  I left it to download some podcasts overnight and when I came back down in the morning, it was a the login.  I didn't think much of it, then it did it again when I got home from work.

Anyhow, I'm glad every thing's back to normal.

---

