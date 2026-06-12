---
title: "Resize extra panels in KDE?"
date: 2007-01-31
forum: General Help
---

### Post by tnunamak on 2007-01-31
I added a new panel at the bottom of my screen, but I can't resize it. Right click --> configure panel only allows me to adjust the size of the main panel. Is there a way I can configure all of them?

---

### Post by Jucato on 2007-01-31
It's a bug since KDE 3.5.5. You just need to restart your panel so that you can configure each of them. To restart it, press Alt+F2 and enter the following command:

```
dcop kicker kicker restart
```

---

