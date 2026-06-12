---
title: "Is there a way to do this...?"
date: 2007-05-21
forum: General Help
---

### Post by EvenStevens on 2007-05-21
When I launch a Windows app through wine fullscreen (which forces my screen to run at a lower res than native - but that's just the program), my Beryl window effects make the menus in the program mess around with the screen when a new menu pops up.
Right now I have the "burn" effect on to close windows. 
When I select a new item in the menu, the burn effect sticks around and causes black lines and such to appear for a few seconds after the new menu has loaded.

If you understood all of that then read on :P

Is there a way for my Window manager to change from Beryl to Compiz or Metacity when just that program loads? Obviously these programs don't have the crazy effects and so won't screw around with my menus.
Then when I quit out, Beryl takes over again.

I just think it's too much hassle to change the Window manager every time I start and quit the app.

Thanks!

---

### Post by nerdman978 on 2007-05-21
You could ditch the burn effect if it bothers you that much.

---

### Post by EvenStevens on 2007-05-21
But I like it on everything else >_>

---

### Post by steevols on 2007-05-21
Well, you could write a small script and place it in your quick-launch area or on the desktop, containing something like

"beryl --replace" or "metacity --replace", etc. I don't know if that would work, but it should be a start.

---

