---
title: "desktop"
date: 2007-10-07
forum: General Help
---

### Post by fred0843 on 2007-10-07
How do I keep mounted Partitions from showing up on the desktop Ubuntu? Want them to mount ,but not show up on desktop.

---

### Post by aJayRoo on 2007-10-07
Press Alt-F2 and type:
```
gconf-editor
```
into the run dialog. When gconf-editor loads up use the left hand panel to navigate to 'apps -> nautilus -> desktop' and uncheck the 'volumes visible' key. Mounted volumes will no longer be displayed on the dekstop.

---

