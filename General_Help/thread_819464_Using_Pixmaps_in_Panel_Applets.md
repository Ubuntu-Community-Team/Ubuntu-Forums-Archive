---
title: "Using Pixmaps in Panel Applets"
date: 2008-06-05
forum: General Help
---

### Post by guyminuslife on 2008-06-05
I have been trying to get pixmap backgrounds (preferably with an alpha channel) for my window selector button applets on my Gnome panel for a while. I can change their background to a solid color fairly easily using .gtkrc-2.0, but when I try to use a pixmap instead of a solid color, it doesn't work.

My .gtkrc-2.0 file looks like this:

```
style "panel" {
	fg[NORMAL] = "#ffffff"
	fg[PRELIGHT] = "#000000"
	fg[ACTIVE] = "#000000"
	fg[SELECTED] = "#000000"
	fg[INSENSITIVE] = "#8A857C"

	bg[NORMAL] = "#00ff00"
	bg[PRELIGHT] = "#00ff00"
	bg[ACTIVE] = "#00ff00"
	bg[SELECTED] = "#00ff00"
	bg[INSENSITIVE] = "#7099cc"

#	bg_pixmap[PRELIGHT] = "/home/guyminuslife/.mythemes/buttonbgselected.png"
#	bg_pixmap[ACTIVE] = "/home/guyminuslife/.mythemes/buttonbgselected.png"
#	bg_pixmap[SELECTED] = "/home/guyminuslife/.mythemes/buttonbgselected.png"
#	bg_pixmap[INSENSITIVE] = "/home/guyminuslife/.mythemes/buttonbgselected.png"


}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
```

As is, it changes the background colors of the panel applets I want to change. But if I comment out the background color attributes and uncomment the pixmap attributes, then it just goes to the default Gnome background, which looks ugly with the rest of my desktop.

A couple more things to note:
1) I am able to use pixmaps for other things, like the Gnome panel itself. 
2) I tried using a very large pixmap as the background for the applets, and while it didn't show up, it took an especially long time to load, which makes me suspect that it's loading the pixmaps, just not displaying them.
3) When starting certain applications from the terminal (when trying to use pixmaps), I get the error message: ```
/home/guyminuslife/.gtkrc-2.0:46: Unable to locate image file in pixmap_path: "/home/guyminuslife/.mythemes/buttonbgselected.png"
```


Sorry if this is long. Any help would be appreciated.> 

---

