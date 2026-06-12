---
title: "Editing Gnome's menu -- Hardy won't let me"
date: 2008-05-07
forum: General Help
---

### Post by pspotts on 2008-05-07
I'm trying to edit my Gnome menu by right-clicking on Applications and selecting Edit Menus. I find that under Hardy, I can do far less that I could under Feisty. Perhaps I'm missing some package, or more-intrusive editing requires a permissions change. But at this point, editing the menu as user only allows me to check or uncheck individual items. I can't find a way to set up new categories or move items from one category to another the way I could as user under Feisty. What blindingly obvious step am I missing?

With best regards,

Pete

---

### Post by mgol on 2008-05-18
I got it! Just:
```
sudo apt-get install smeg
```
It automatically restores usual advanced menu editor.
I hope it also helps You, pspotts. :)
You can also use:
```
sudo apt-get install alacarte
```

---

