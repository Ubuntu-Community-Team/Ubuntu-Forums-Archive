---
title: "Clicking desktop causes Conky to disappear behind Komorebi, want to keep Conky on top"
date: 2021-03-16
forum: General Help
---

### Post by Cursed Lemon on 2021-03-16
Hey guys, super nitpicky problem here. I'm running both Komorebi and Conky, the former because it's the only Linux-based solution I know of for animated wallpapers. As I have it now, upon startup Conky will load after a brief sleep script and display on top of my animated wallpaper. However, if I click the desktop anywhere, Komorebi will come into "focus" and Conky will disappear behind it, forcing me to kill + relaunch the application if I want to get it back. 

I know there's ways to make Conky visible on top of *everything* including windows, but is there any way to specifically pin an application to the top/bottom of the desktop only? Some kind of compositing feature or launch arguments?

EDIT: FWIW, I also have Cairo Dock running and Cairo Dock does not fall behind Komorebi

---

### Post by deadflowr on 2021-03-17
What does the conkyrc show?

> but is there any way to specifically pin an application to the top/bottom of the desktop only? 
Depends on the window manager in use, probably.
I know it's doable with compiz, but I'm not sure with what Ubuntu now uses, mutter.
You can probably finagle the wmctrl program to do this, though.

---

### Post by Cursed Lemon on 2021-03-17
> **deadflowr said:**
> What does the conkyrc show?

own_window, window type, etc. are all left default, not sure if any other variable would matter in this case

> Depends on the window manager in use, probably.
I know it's doable with compiz, but I'm not sure with what Ubuntu now uses, mutter.
You can probably finagle the wmctrl program to do this, though.

I'm running Xubuntu so it's xfwm. [This]("https://forum.xfce.org/viewtopic.php?id=8231") thread offers an idea, I'll try it later on and see, hopefully it doesn't stick Conky on top of my open windows.

---

### Post by CatKiller on 2021-03-17
> **Cursed Lemon said:**
> I'll try it later on and see, hopefully it doesn't stick Conky on top of my open windows.

I haven't checked what that thread is suggesting you do, but I think the window manager hints would be applied to Komorebi rather than Conky; Komorebi would get the "desktop" hint and Conky would get the "keep below" hint, which keeps it below everything that isn't the desktop.

---

### Post by berndmj on 2021-08-25
> **Cursed Lemon said:**
> own_window, window type, etc. are all left default, not sure if any other variable would matter in this case

My conky has this
```
own_window_type = 'desktop',
own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
```

I had to insert that because clicking anywhere on the desktop made my conky disappear.

Hope this helps ...

---

