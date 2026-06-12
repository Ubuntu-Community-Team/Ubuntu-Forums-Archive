---
title: "upgraded emacs-snapshot, info nodes are now missing"
date: 2007-10-31
forum: General Help
---

### Post by BattlePanic on 2007-10-31
This morning Ubuntu Gutsy notified me of an emacs-snapshot update, so I elected to install the update.

I just noticed that GNU info is missing the emacs-related info nodes.  They still appear to be on my disk under /usr/share/info/emacs-snapshot but they aren't appearing in info's topmost directory.  I suspect the emacs-snapshot update had something to do with it.

I find myself always having to refer to the emacs documentation so these info nodes are essential.  Anyone have any ideas of why these nodes may have disappeared and more importantly, is there a quick way to restore the emacs-related info nodes?

---

### Post by BattlePanic on 2007-11-01
Well after some digging around it appears that info's topmost directory is stored in a file called /usr/share/info/dir.  Imagine that.  In my particular installation there is a file named "dir" and also a file named "dir.old" Both files are missing a reference to the all-important emacs info file.  Looks like I'll have to make an entry manually.  Why this entry went missing in the first place is still a mystery.

---

