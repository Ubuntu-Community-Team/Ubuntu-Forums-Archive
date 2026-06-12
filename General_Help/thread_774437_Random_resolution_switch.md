---
title: "Random resolution switch"
date: 2008-04-29
forum: General Help
---

### Post by barboachtraner on 2008-04-29
I've been using 1280x1024 resolution with no trouble for a while, but when I booted up today, strangely, my resolution had changed to 1792x1344 and I had to scroll the edges of the screen to find the GNOME panel. I changed it back right away, logged in again and it was fine, but I'd like to know if there's any particular reason why this happened. I did encounter some wonkiness with 915resolution and my Intel video card shortly after installing Ubuntu, but haven't had any problems like that recently.

---

### Post by sujoy on 2008-04-29
check /etc/X11/xorg.conf for 1792x1344 in the Display Section, if its there , then delete it and restart the xserver

---

