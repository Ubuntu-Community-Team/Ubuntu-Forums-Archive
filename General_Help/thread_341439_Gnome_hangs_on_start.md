---
title: "Gnome hangs on start"
date: 2007-01-18
forum: General Help
---

### Post by ryanc on 2007-01-18
I rebooted this morning and logged in through gdm. Gnome started to load (the gnome splash in the middle of the screen came up, and displayed the first icon (for the window manager?) and it just hangs there. After giving it 15-20 minutes to complete I gave up and restarted gdm. I started starting with the safe gnome session and the same thing happened however I got a blank grey dialog in the top left of the screen.

Since then I have installed kde via the console and have been using it however I would like gnome back. Does anyone know what might be wrong?

---

### Post by zerwas on 2007-01-18
Hello ryanc,

You could give us the output of the file .xsession-errors in your home-directory.

A solution to solve this problem could be to add a new user and trying to log in with him.
You can do this by entering
```
sudo users-admin
``` in a terminal.

regards,
zerwas

---

### Post by ryanc on 2007-01-18
Thanks for your input. I went to do what you asked and now I am able to login to gnome without issue. I suspect the issue had something to do with network manager trying to configure my wireless card (my work recently changed wireless settings) and hanging waiting on that to continue?

If I experience any more issues I will report back with the .xsession-errors content.

---

