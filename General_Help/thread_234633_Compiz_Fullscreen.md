---
title: "Compiz Fullscreen?"
date: 2006-08-11
forum: General Help
---

### Post by BitTorrentBuddha on 2006-08-11
How can I set a key in compiz to make a window fullscreen? With metacity it was as simple as editing the keyboard shortcuts, any help would be appreciated. I would like to have Azureus running fullscreen on one of the cube's faces.

---

### Post by hopstah on 2006-08-11
alt+f10 does it for me.  but if you want to change it, open gconf-editor, and go to apps > compiz > general > allscreens > options, and change the value for the key 'maximize_window_key'

---

### Post by BitTorrentBuddha on 2006-08-11
I meant fullscreen as in when you press 'f' while watching a movie in totem, not maximized.

---

### Post by teich on 2007-11-24
I'm having the same issue.  I'd like a fullscreen mode which makes the window content cover the entire face of the cube, i.e. so one face of the cube looks like a terminal when running without gdm.  I'm a little annoyed that upgrading to 7.10 (and therefore replacing beryl with compiz) has now made this impossible.

Is there a way to do this with compiz?

Thanks.

---

### Post by teich on 2007-12-07
I randomly stumbled across it today - "Extra WM Options" has the appropriate option.  Note that for true fullscreen goodness you need to force the window to always be on top, or else  the Applications, etc. bar at the top will sometimes end up on top of the window you want to be fullscreen.

---

