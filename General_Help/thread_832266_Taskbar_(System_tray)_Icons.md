---
title: "Taskbar (System tray) Icons"
date: 2008-06-17
forum: General Help
---

### Post by pb_online on 2008-06-17
By default, icons are seperated on two lines...

[http://www.imageshack.gr/view.php?file=op73wtmwmddi0t0gc392.png](http://www.imageshack.gr/view.php?file=op73wtmwmddi0t0gc392.png)

When I open a new program, icons sort on one line...

[http://www.imageshack.gr/view.php?file=7xrsspwvm6b0vemfiqbo.png](http://www.imageshack.gr/view.php?file=7xrsspwvm6b0vemfiqbo.png)

Why this happens? I want them always on two lines.

---

### Post by Zorael on 2008-06-17
It's a semi-known bug; the kicker tray applet sometimes doesn't enforce icon size, allowing certain apps' icons to end up bigger than the other ones. Often big enough to break the two-row look.

Workaround, posted at [http://ubuntuforums.org/showthread.php?t=612938](http://ubuntuforums.org/showthread.php?t=612938):
> **harold4 said:**
> When I open pidgin, I use the following script.  It's ugly, but it works.  
```

#!/bin/sh
pidgin
dcop kicker Panel setPanelSize 24
dcop kicker Panel setPanelSize 54

```
Just make sure to set the second number (54 above) to the size you use for your kicker panel. I use 54, Large is 58, Normal is 46.

---

### Post by pb_online on 2008-06-17
hmmm...

Can I set the size of icons, the same as the icons on Quick launch?
They will be smaller, so there is no chance to unsplit on one row :)

---

### Post by Zorael on 2008-06-17
I don't think so, likely only if you manually tinker with the source code to the current KDE3 tray applet.

---

