---
title: "Stupid question - Toolbar is on side now"
date: 2008-05-08
forum: General Help
---

### Post by drunkmatador on 2008-05-08
Accidentally clicked something, not sure what, and now my toolbar (the one normally on top with applications, places, etc.) is on the left side of my screen. I'm sure it's something easy to get it back on top but I'm not sure what.. any help?

---

### Post by tamoneya on 2008-05-08
left click and drag it to where you want.

---

### Post by Statix0 on 2008-05-08
Can you not click it and drag it back to the top? I haven't used gnome in a while so I don't remember, but I think you can.

If not try looking for unlock toolbar or something when you right click it.

---

### Post by drewcoon on 2008-05-08
Right click > Properties > Orientation = Top :)

---

### Post by drunkmatador on 2008-05-08
Oh cool, thanks a lot. Before when I right clicked I was doing it on the wrong section, I guess, and it was only coming up with a Preferences menu but not Properties.

Got it.

---

### Post by drunkmatador on 2008-05-24
Ok now I'm having the same problem and can not fix it. Everywhere on the toolbar is already covered by something, so when I right click it comes up with a different menu than I need to go to Properties. Is there a way I can go into preferences and reach this menu in a different way?

---

### Post by tcommbee on 2008-05-24
You could try the following:
start gconf-editor (should be under Applications/System tools).
There you navigate to /apps/panel/toplevels were you should see to "folders" a la "bottom_panel_screen0". Selecting one of them, you can set the key "orientation" to whatever you want (given you want either "top","left","bottom" or "right").

---

### Post by drs305 on 2008-05-24
```
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation "top"
```

I made a shortcut after what you described happened to me. Since I didn't have a blank space on the panel to click on, I deleted an unused icon and just added an icon with the above command. Now I don't need any blank space to get the panel back to the top. I just click the icon  ;-)

---

### Post by strabes on 2008-05-24
Does this happen regularly to you guys?

---

### Post by drunkmatador on 2008-05-25
For some reason, yes. But I think every time has been when a friend was using my laptop, so I'm not sure what the cause of it was. Could of been something they did.

Thanks for the code drs305, worked great! :)

---

### Post by drs305 on 2008-05-25
> **strabes said:**
> Does this happen regularly to you guys?

It doesn't happen often to me. I have found that sometimes the mouse pointer will 'grab' the panel and move it unexpectedly to the side or bottom if my pointer hangs over the panel for a few seconds and then I move it rapidly. There is no rt or left clicking involved when this happens.

It only took me one time when I didn't have any blank area to click on to restore it to the top before I made the shortcut icon ](*,)

---

### Post by diablo75 on 2008-05-25
> **strabes said:**
> Does this happen regularly to you guys?

Seems to be a little bug (I've experienced this anyway) where the mouse seems to be stuck after clicking on an icon on the taskbar (like the firefox shortcut for instance).  The icon doesn't actually get clicked on, but out of reflex, you move your cursor away from the task bar and you're icon is in that "hand" mode, and you discover you have to click again to release the bar, otherwise you'll drag it to a different edge of the screen by accident...

---

### Post by tcommbee on 2008-06-04
Confirmed. If you double-click on an icon and don't release the button the second time, you grab the panel (maybe the icon is unresponsive for a while). If you somehow manage to move the mouse to another screen border without releasing the button, you move the panel. Don't know if this is a bug, as it is highly unlikely to move the mouse this far by accident (except maybe if the icon is close to a screen corner).

---

### Post by niceguy123 on 2008-12-04
> **drs305 said:**
> ```
gconftool-2 --type string --set /apps/panel/toplevels/top_panel_screen0/orientation "top"
```

I made a shortcut after what you described happened to me. Since I didn't have a blank space on the panel to click on, I deleted an unused icon and just added an icon with the above command. Now I don't need any blank space to get the panel back to the top. I just click the icon  ;-)

&#8206;&#8206;Thanks.

---

### Post by tcommbee on 2008-12-04
Since Ubuntu 8.10 you can lock a panel in place by right-clicking on an empty part of it and activating the option.

---

