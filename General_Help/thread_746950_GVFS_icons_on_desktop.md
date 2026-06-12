---
title: "GVFS icons on desktop"
date: 2008-04-06
forum: General Help
---

### Post by jazzor on 2008-04-06
currently when using gvfs on gnome 2.22, it will display icons for all mounts including loop mounts and what not, and i cannot see any obvious way to hide these icons. Would someone enlighten me as to how such an obvious feature got left out (not that its ubuntus fault, just generally annoyed at how the gnome team does away with any configurability whatsoever)? and how to hide the icon?

---

### Post by cgitz on 2008-04-08
I've also been searching for a way to hide the gvfs icons from the desktop - yours is the only related post that I've found.

It isn't such a big deal for me - I keep the location bookmarked and just unmount it when I'm done (right-click the desktop icon, unmount) - then the desktop icon goes away.  I'm sure you're already aware of that.  I would be much happier if I could keep the icon from appearing in the first place.

Good luck - I'd like to see a solution, too.

---

### Post by cgitz on 2008-04-26
I stumbled onto the solution.  I was reading an article called "10 Tips for After You Install or Upgrade Ubuntu".  One of the tips was [Hide Partition Icons From Your Ubuntu Desktop]("http://tombuntu.com/index.php/2007/10/25/hide-partition-icons-from-your-ubuntu-desktop/").

<alt><f2>
Run Application: gconf-editor
Browse to "apps->nautilus->desktop"
Uncheck "volumes_visible"

Unchecking "volumes_visible" prevents icons linking to mounted volumes from appearing on the desktop.

It was easy to unmount volumes from the desktop icon but it can still be done from Nautilus. If you open Nautilus to any location (your home folder), mounted drives are still displayed in the Side Pane (left) under Places.  You can right-click any mounted volumes and unmount them.

Hope this helps.

---

