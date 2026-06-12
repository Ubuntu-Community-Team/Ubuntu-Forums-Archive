---
title: "Massive Login Letters"
date: 2008-03-21
forum: General Help
---

### Post by jpoRS on 2008-03-21
Hey,

Strange problem.  Whenever I go to the login screen, the username and password circles are HUGE.  Like 72 pt. font.

Not a terribly worrying problem, just weird.

thanks,
jim

---

### Post by learning on 2008-04-26
I have this problem too.  Any fix?

---

### Post by jpoRS on 2008-04-28
I reset my video card/monitor information.  Turns out I was set to an experimental video card (which I don't have) and a low resolution monitor setting.  After all the mucking about in terminal I went through, turned out to be just a few clicks and presto!

To change the settings:

System > Administration > Screens and Graphics Preferences
From here select the correct monitor and graphics card, reboot and you're in the clear.

Tips: 
-If your monitor isn't one of the one's listed, just select a "Generic" of appropriate resolution.
-If you have a widescreen monitor, be sure to check the box in the monitor selection window.
-If your video card isn't listed, pick the closest relative card.  I don't know if this is foolproof, but it worked for me.

Let me know if I can do anything else.

jim

---

### Post by siblog on 2008-04-28
I was having the same issue and I couldn't find "Screens and Graphics Preferences" in my menu. I even used "Main Menu" under preferences to see if it was hidden, but I still could not find anything. I finally just found the terminal command to get the Screens and Graphics Preferences window -  gksu displayconfig-gtk

Anyways this seemed to fix it. Thanks

---

### Post by siblog on 2008-05-01
Oh nevermind maybe it didn't fix it :-/

---

