---
title: "Assign Expo Key Hotkey to Side Mouse Buttons"
date: 2014-10-12
forum: General Help
---

### Post by fohrums on 2014-10-12
**HARDWARE**:
Mouse - Zowie FK
[B]
SITUATION:[/B]
[I]If i'm not mistaken Ubuntu; using the x-windows framework, only allows and therefore limits each key to have one function and no more?
    So, that means I won't be able to assign the 'Expo Key' (Ubuntu's view all workspaces) to more than one hotkey, due to this limitation?[/I][INDENT] [U]

First[/U], I needed to find out how the extra mouse buttons were assigned using 'xev'. This will bring up a small window with a square outline in it, just focus that window and press keys to find out the binding-attribute (filtering the mass info it gives you, generally your looking for a number which is in parenthesis).
[/INDENT]
 
```
$ xev
```
[INDENT]_Second_, I found out that my 2-side buttons on the left side work but not on the right (4-total) which is fine in this case as I only want to use one of them; button 8.
[/INDENT]
 
[[IMG]http://s28.postimg.org/h67e1w2q1/Untitled.jpg[/IMG]]("http://postimg.org/image/h67e1w2q1/")[INDENT][U]

Lastly[/U], I don't know how to assign this 'button 8' to replace <Super>+S which is the default Expo Key. Ubuntu's Keyboard shortcut settings only refers to the keyboard and not the mouse, so it's handler doesn't detect anything coming from my Zowie (xev does).




[/INDENT]
**OTHER NOTES:**
using ccsm's Expo plugin to change the hotkey doesn't detect my mouse's extra buttons aswell.

---

