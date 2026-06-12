---
title: "Can I have Kontact's and Evolution's PIM information synced all the time?"
date: 2007-05-30
forum: General Help
---

### Post by wersdaluv on 2007-05-30
I prefer Kontact as my PIM app, but I found out that synce does not work with Kubuntu Feisty, but it works if you sync a Pocket PC with KDE.

Is there such a way that will make Evolution's and Kontact's PIM information synced all the time?

---

### Post by wersdaluv on 2007-06-07
I found the solution out. All I had to do was to add ```
/home/user/.evolution/calendar/local/system/calendar.ics
``` and
```
/home/allan/.evolution/tasks/local/system/tasks.ics
```
in Kontact's Calendar resource so that Kontact will use Evolution's Calendar! :)

---

