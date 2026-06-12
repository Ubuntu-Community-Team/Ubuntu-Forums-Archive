---
title: "Trying to get rid of tooltips in Hardy"
date: 2008-04-24
forum: General Help
---

### Post by hackle577 on 2008-04-24
I tried the method using gconf (apps > panel > global) but that appeared to have no effect. Any tips?

---

### Post by Ub1476 on 2008-04-24
It's a bug, which none has cared to fix (it's been present for far too long..). If you use Compiz, you can set opacity of tooltips to 0, or use a dock instead of a panel.

---

### Post by hackle577 on 2008-04-24
How do I turn the opacity down with Compiz? Can't find the setting.... :-(

---

### Post by Ub1476 on 2008-04-24
If Advanced Desktop Effects isn't installed..:

```
sudo apt-get install compizconfig-settings-manager
```

Now open ccsm>General>Opacity>Add>

name=tooltips #This will hide all tooltips
opacity=0

---

