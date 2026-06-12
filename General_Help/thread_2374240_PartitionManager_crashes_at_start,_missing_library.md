---
title: "PartitionManager crashes at start, missing library?"
date: 2017-10-13
forum: General Help
---

### Post by timonoj on 2017-10-13
Hi guys,

I can't start the KDE partition manager. It complains about the missing library pmlibpartedbackendplugin.
> 
sudo partitionmanager
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
Could not load plugin for core backend  "pmlibpartedbackendplugin" :  "The shared library was not found."
Could not load plugin for core backend  "pmlibpartedbackendplugin" :  "The shared library was not found."
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2
XmbTextListToTextProperty result code -2


Any ideas of this? My google search didn't find much valuable...

---

### Post by timonoj on 2017-10-13
...Nevermind. Found the issue. 
Seems there was a bug in the last update and kpmcore was just a suggested package, not a needed dependency. I manually installed kpmcore and it works correctly now.

---

### Post by Bucky Ball on 2017-10-14
Great. :) Please mark thread as 'Solved' from 'Thread Tools' at top right to help others.

---

