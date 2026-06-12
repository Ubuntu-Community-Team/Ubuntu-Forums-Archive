---
title: "Using xmodmap to bind a key-combo"
date: 2008-04-22
forum: General Help
---

### Post by sadris on 2008-04-22
I am currently attempting to remap my capslock key to Control+Backslash. Is this possible with xmodmap or can I only remap it to just plain backslash? 

I am currently doing:
```
xmodmap -e "remove lock = Caps_Lock"
xmodmap -e "keycode 66 = backslash"
```

This makes my capslock key send a backslash, but I want it to send Control + backslash.

---

### Post by sadris on 2008-04-25
bump?

---

### Post by stairwayoflight on 2008-06-09
Try xkeycaps, install it from synaptic.

If you right-click on a key to edit its keysym's, there is a list of modifiers you can enable, including control. I haven't tried it, but it may work for you (ie. set the key to '/', turn on the control modifier bit).

It will generate a file you can activate with xmodmap on startup. I'm just not sure which file to run the xmodmap command from though ;-)

---

