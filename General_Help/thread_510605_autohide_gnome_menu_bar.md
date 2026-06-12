---
title: "autohide gnome menu bar"
date: 2007-07-26
forum: General Help
---

### Post by dje on 2007-07-26
Is it possible to make the gnome menu bar/s disappear completely when on autohide? Also can they be hidden behind open windows so applications can gain a full screen?

---

### Post by raja on 2007-07-26
When the panels are not autohidden, you cannot have windows over them.
However you can set the autohide size to 0 from default 6 in gconf if you want them to disappear completely when you autohide them. 
You might be interested in looking at [this]("http://reachbeyondgrasp.blogspot.com/2007/04/hide-and-show-panels-with-keyboard.html") too.

---

### Post by dje on 2007-07-26
thanks raja but how do i set it from 0 to 6 in gconf, how do i get to gconf?

edit: also is there a way to speed up the time it takes for the panel to appear?
edit 2: found out how to set it to 0

---

### Post by raja on 2007-07-26
```
gconf-editor
```
to open the gconf-editor.
Then navigate to '/apps/panel/toplevels/top_panel_screen0' and change 'auto_hide_size' to 0.
Or you can just paste this in the terminal ```
 gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/auto_hide_size" --type integer "0"
```

---

### Post by dje on 2007-07-26
Thanks ive got it setup just how i want it

---

