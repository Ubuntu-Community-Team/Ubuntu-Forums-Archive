---
title: "decide where to open terminal"
date: 2006-11-24
forum: General Help
---

### Post by ZiTriX on 2006-11-24
How do I do to decide the cordinats to where the gnome-terminal shall apear on the screen?

Glad for answer :)

---

### Post by mcduck on 2006-11-24
You could make a new launcher on your panel with something like this as command:
```
gnome-terminal --geometry=46x18-16+43
```

Just change the geometry to your liking. The easy way to get numbers for that is to resize your terminal and move it where you want it, then run 'xwininfo' and click on the terminal window, you'll see the geometry from xwininfo's output.

---

