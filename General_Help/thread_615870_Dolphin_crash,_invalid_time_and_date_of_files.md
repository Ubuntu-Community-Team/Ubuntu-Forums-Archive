---
title: "Dolphin crash, invalid time and date of files"
date: 2007-11-17
forum: General Help
---

### Post by Zorael on 2007-11-17
I have this folder that Dolphin always crashed upon entering. Konqueror and other "explorers" can handle it fine. There's some interesting terminal output.

```
zorael@azrael:/media/main/random/folder$ dolphin .
QInputContext: no input method context available
QInputContext: no input method context available
QDate::setYMD: Invalid date -53328--528--528
QTime::setHMS Invalid time -528:-528:-528.000
QDate::setYMD: Invalid date -53328--528--528
QTime::setHMS Invalid time -528:-528:-528.000
QObject::connect: Cannot connect (null)::contentsMoving(int, int) to DolphinView::slotContentsMoving(int, int)
KCrash: Application 'dolphin' crashing...
```

Is there some terminal way to manually change the creation/changed time and date of files?

---

### Post by Zorael on 2007-11-23
Bumpity bump.

---

