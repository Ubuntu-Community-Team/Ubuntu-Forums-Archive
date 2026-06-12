---
title: "Tracker"
date: 2007-10-23
forum: General Help
---

### Post by geeree on 2007-10-23
Hello,

Could somebody please explain how to use Tracker, if it keeps on exiting with this error? —
```

Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...

** (trackerd:8459): WARNING **: Cannot open or create lockfile - exiting

[1]+  Exit 1                  trackerd

```

The Tracker home page did not help. 

Girish.

---

### Post by jamiemcc on 2007-10-24
Simply delete the lock file in ~/.local/share/tracker

This is only likely to occur if your computer lost power while tracker was running and it did not delete the lock file itself on exit

---

