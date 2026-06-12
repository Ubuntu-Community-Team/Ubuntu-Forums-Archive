---
title: "Key remapping and evdev"
date: 2018-03-01
forum: General Help
---

### Post by plkoij on 2018-03-01
I have 16.04 on my laptop. I'm trying to remap a whole bunch of keys.
' 
Based on [https://medium.com/@damko/a-simple-humble-but-comprehensive-guide-to-xkb-for-linux-6f1ad5e13450](https://medium.com/@damko/a-simple-humble-but-comprehensive-guide-to-xkb-for-linux-6f1ad5e13450), I changed /usr/share/X11/xkb/keycodes/evdev. For example, I changed the line "<RGHT> = 114;" to "<DOWN> = 114;", intending to turn my right arrow key into a down arrow key. My understanding was that whenever the keyboard sent the keycode 114, it would immediately be interpreted as DOWN instead of RGHT. This works fine in some cases, with the exception being using CTRL+ALT+arrow keys to move between workspaces. When I do CTRL+ALT+[the key I remapped in this example] it behaves like CTRL+ALT+RGHT, not CTRL+ALT+DOWN like I would expect.

I don't need any practical advice, I'm going to restore the original evdev file. But I am curious where my misunderstanding is.

---

