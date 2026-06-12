---
title: "gset-compiz help"
date: 2006-07-25
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-07-25
I just installed xgl/.compiz. I must say it rocks, though I don't fully know the controls, if maybe anyone has a guide or something.

Anyway I was messing with gset-compiz, in the "wobbly" tab, and i messed it up. Does anyone know the original settings? right now I can't use it cause it takes 30 secs for the windws to stop moving.

any help would be appreciated.

---

### Post by _simon_ on 2006-07-25
lol I'm not sure if mine are original but they work:

GRAB
Friction: 3.0
Spring k: 8.0

MOVE
Friction: 3.0
Spring k: 8.0

MAXIMISE
Friction: 0.8
Spring k: 0.3

RELEASE
Friction: 2.8
Spring k: 8.0

MAP
Friction: 0.8
Spring k: 0.8

FOCUS
Friction: 3.0
Spring k: 8.0

VISUAL BELL
Friction: 3.0
Spring k: 8.0

Down the right hand side I only have the following checked:

map shiver effect
maximise effect

GRID RESOLUTION: 7
MIN GRID SIZE: 8

WINDOWS TYPES

Normal: Map & Move
Dialog: Map & Move
Utility: Map & Move
Menu: Map & Move
Toolbar: Map & Move
Splash: Map
Modal Dialog: Map & Move
Dock: Map
Desktop: Map
Fullscreen: Map
Unknown: Map

---

### Post by s_h_a_d_o_w_s on 2006-07-25
Thank you so much! It works again!

---

### Post by s_h_a_d_o_w_s on 2006-07-25
Do you know how to change the window border in compiz?

---

### Post by _simon_ on 2006-07-25
You need to go into Theme Selector then edit, the options are there :)

This is assuming of course that you are using Quinns packages - the red cube in the system tray...

---

### Post by testube_babies on 2006-07-25
Just in case you ever need the defaults again, you can set compiz back to its defaults by doing this from a terminal:
```
gconftool-2 --recursive-unset /apps/compiz
```
You can change /apps/compiz to /apps/compiz/plugins/wobbly (for example) if you want to reset only the wobbly plugin.

And the theming tool is in System -> Preferences -> Compiz Themer if you use Quinn's repository.

---

