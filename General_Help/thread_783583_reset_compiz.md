---
title: "reset compiz??"
date: 2008-05-05
forum: General Help
---

### Post by gschoppe on 2008-05-05
I used sudo apt-get install "compizconfig-settings-manager" to get the "advanced desktop effects settings", and after fooling with the tool, have messed up my GUI in two BIG ways...

[LIST=1]
[*]All of my tray icons are now appearing in their own mini windows that appear to be locked to the upper left corner of the desktop
[*]my title bars have totally disappeared, and all windows appear (and are stuck) in the upper left hand corner
[/LIST]

Is there a way to reset compiz to defaults??

alternatively, does anyone have any idea what I did?

---

### Post by FakeOutdoorsman on 2008-05-05
You can try to remove the compiz settings.  I don't have compiz installed, but you can try:
```
mv ~/.compiz ~/.compiz_original
mv ~/.emerald ~/.emerald_original
```
This will move your old compiz and emerald configuration settings.  When compiz/emerald restarts they should build a new default config directories.

Then log out and back again:
ctrl + alt + backspace

---

### Post by gschoppe on 2008-05-07
that, along with a little more compiz tinkering, fixed the title bar issue, but I still have all my tray icons displaying in their own little unmovable windows in the upper left corner of the screen... 

any other ideas?


BTW, the emerald folder doesn't exist, and I had to manually edit the compiz settings, rather than remove them, because after removal, nautilus refused to start right.

---

