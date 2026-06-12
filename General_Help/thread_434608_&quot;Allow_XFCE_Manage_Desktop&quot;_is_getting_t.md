---
title: "&quot;Allow XFCE Manage Desktop&quot; is getting turned off by Right click."
date: 2007-05-06
forum: General Help
---

### Post by Koori23 on 2007-05-06
Weird Problem. I'm running XUbuntu Feisty and for some reason, when I right click, it turns off my backdrop to some strange grayish olive green color. If I did this, I don't know how I did it. I also don't know how to remap the mouse button so it won't do that. 

I did attempt to save my session at logout, and it's still doing it.

---

### Post by angryhomer17 on 2007-05-07
I'm not exactly sure if you are saying right clicking disables xfce management and nothing happens, or you get a different menu, or it just changes the background. Try this though:

i had a similar problem, though I don't remember if my background changed. I think it went to the default gnome background. If you still have gnome installed and only want to use xfce, I would suggest removing all gnome packages that you dont use. 

For a quick fix this may help: Right click on the desktop> settings> settings manager > desktop> then check "allow xfce to manage desktop"

If you can't do a right-click without something going wrong open a terminal and type:

```
xfce-setting-show
```

That will bring up the settings manager too. Hope this helps.

---

### Post by romojap on 2008-05-14
I'm having the same problem.

I'm running Xubuntu 8.04.  When I right-click my desktop, my wallpaper disappears, and the usual menu doesn't pop up.  When I check in desktop settings, I find that the "Allow XFCE to manage desktop" button is unchecked.  I check it, then my desktop returns to normal.  I then right-click on the desktop, and it unchecks the box automatically.

I'm scratching my head here...

---

### Post by charding on 2008-05-16
I'm having the same problem. I think nautilus is starting and grabbing the dsktop. When I go to Settings->Settings Manager->Desktop the 'Allow xfce to manage desktop' box is always unticked. Even when I save my session when logging out it doesn't save it..

---

