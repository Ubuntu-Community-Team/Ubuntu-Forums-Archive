---
title: "[SOLVED] Cheap trick for resolution fix on DLP widescreen tv"
date: 2008-06-15
forum: General Help
---

### Post by Jebtrix on 2008-06-15
I use a 50inch Samsung DLP projection TV for my monitor. It was a complete pain in the a** to get it working perfectly in windows with PowerStrip but I got it eventually. It uses a VGA connection and ends up being a really weird custom resolution to fit exactly. I've tried several times to get the resolution to work under linux and given up for the time being. As it is now I got some overscan.

My cheap trick to fix it is to just add some more panels to the gnome desktop on all corners to create margins and set panels to transparent. Works great but with 2 side effects keeping it from being perfect. 
1. Panels only resize down to 23 pixels (need it to around 13 pixels)
2. Transparent panels still show drop shadow at edge

So is there a way to force gnome's panel width even smaller and hide the drop shadow effect? I'd settle for a width fix :)

---

### Post by chewearn on 2008-06-15
**1. Workaround to create 13px width panel**

Open gconf-editor, by pressing ALT+F2, and type in "gconf-editor", and click [Run].

Go to the following key:
apps > panel > toplevels

Find/select the panel key that correspond to the panel.

Select auto_hide checkbox.  The panel will now hide itself, leaving 6px on the screen.  Incidentally, this will also tells you that you are working on the correct panel.

Change auto_hide_size to 13, to give you 13px width.

Change unhide_delay to a large value, so the panel will take a long time to unhide, say 10000 (10 seconds).


**2. Remove panel drop shadow**

Open CompizConfig Settings Manager, find Window Decoration plugin.

Enter the following into the "Shadow windows" box:
(any ) & !(class=Gnome-panel)


.

---

### Post by Jebtrix on 2008-06-16
That did it thank you!

---

### Post by Jebtrix on 2008-07-17
Trick Update:

I encountered a known issue with maximized windows ignoring the right panel (ends up hiding the scrollbar, close button, etc). I messed with window managers but in the end the culprit was the open ATI video driver. Installing ATI's binary video driver did the trick. 

Playing around I found a more flexible method to remove the shadow from the left and right panel while leaving the top/bottom nicely shadowed:

Once you find the panel in gconf-editor by either setting autohide and watching, or looking at the orientation parameter for left/right. You'll notice a name field. I gave the two panels the name: NoShadowPlz 

In compiz > window decorator > window shadows use: 
```
(any) & !(title=NoShadowPlz)
```

---

