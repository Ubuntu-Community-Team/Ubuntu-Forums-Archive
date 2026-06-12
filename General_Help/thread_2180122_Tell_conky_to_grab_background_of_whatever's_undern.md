---
title: "Tell conky to grab background of whatever's underneath it"
date: 2013-10-11
forum: General Help
---

### Post by DrumminngBiker on 2013-10-11
I've got a conky running over my taskbar in ubuntu lucid

If transparency is set in .conkyrc, then it'll grab the background of the root window (as it's supposed to) and look like this:
[ATTACH=CONFIG]246877[/ATTACH]

Anyway to get it to have the background of the taskbar, or is the only way to do it to edit the desktop background image to have a 'fake' taskbar image at the top

---

### Post by mörgæs on 2013-10-13
Lucid is out of support. Before proceeding with the problem it's best to install supported release.

---

### Post by stinkeye on 2013-10-13
Follow mörgæs advice.


Try using argb real transparency.
Set the transparency of the window to 100%.
The valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.
```
own_window yes
own_window_colour ffffff
own_window_title panelconky
own_window_type **panel**
own_window_transparent **yes**
own_window_hints undecorated,sticky,skip_taskbar,skip_pager,**above**
default_color dim gray
**own_window_argb_visual yes**
**own_window_argb_value 0**
```

---

