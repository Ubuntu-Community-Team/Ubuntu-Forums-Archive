---
title: "minimize app to notification area..."
date: 2006-09-28
forum: General Help
---

### Post by markster23 on 2006-09-28
hey guys :) i'm new in ubuntu and i'm just wondering if theres any package or anything i can add to my gnome desktop to minimize any applications to the notifications area.. such as applications that don't have that feature in the settings.. ie. gnome peercast... cuz when i have it open, and i have totem playin a stream, i dont want to have the window open on my task bar.. any ideas ???

---

### Post by DarkN00b on 2006-09-28
If you are looking for something like the Windows "Show Desktop" button, you can add it to any panel by right-clicking the panel and clicking "Add to panel".  Choose the "Show Desktop" applet and drag it to the panel.  Then you right-click the applet and choose "Move". Move the applet to where you want it and left-click once. Then right-click the applet and choose "Lock To Panel".

Whenever you click this icon, all open windows will be minimized to the panel.

---

### Post by markster23 on 2006-09-28
lol thanks but that's not actually what i'm trying to do... i wanna know how i can minimize any programs that i have open to the notification area (system tray, what have you) instead of minimizing them to the taskbar. i know in windows, there are some programs you can download to do that, but i'm not sure in gnome how i'd do it ... but thanx for ur reply none the less!!

---

### Post by DarkN00b on 2006-09-28
No prob & thanks yourself.  I haven't been using Ubuntu long enough to know that myself, so good luck. Maybe someone more experienced can help you.

---

### Post by orb9220 on 2006-09-28
Nope the program has to be written in the code like amarok when you hit the close button it actually minimizes to notification tray.

Or if the program prefs has a feature to enable minimize to notification tray.

Sorry I could be wrong but I don't think so.

---

### Post by honda on 2006-09-29
This seems to do it: [http://ubuntu.wordpress.com/2006/05/24/minimize-any-application-to-the-system-tray/](http://ubuntu.wordpress.com/2006/05/24/minimize-any-application-to-the-system-tray/)
Have not tried it myself

---

### Post by markster23 on 2006-09-29
awesome thanks honda :)

---

### Post by orb9220 on 2006-09-29
Well glad to see one. Wish it was in ubuntu repo's.

And whooaa! I was wrong. Gee me go hide in closet now.

Thanks for the link honda.

---

### Post by Ramses de Norre on 2006-09-29
Alltray does this too and it's in the repo.

---

### Post by Rui Pais on 2006-09-29
> **Ramses de Norre said:**
> Alltray does this too and it's in the repo.

I think it's only on dapper's asher256-repository.
In order to get using apt it needs:
```
deb http://asher256-repository.tuxfamily.org dapper main
```
on your sources.list (don't know if there is on other repos too...).

---

