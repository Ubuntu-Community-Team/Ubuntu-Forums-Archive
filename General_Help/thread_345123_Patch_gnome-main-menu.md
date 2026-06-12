---
title: "Patch gnome-main-menu"
date: 2007-01-23
forum: General Help
---

### Post by hanzomon4 on 2007-01-23
I edited the gnome-main-menu src to remove the text and change the icon to the ubuntu icon. This worked great but I don't have a places tab. I found a [patch]("http://www.ubuntuforums.org/showthread.php?p=1246755&highlight=places#post1246755") that adds the place tab(removes recently used applications) but it fails 5 out of 7 hunks.  I also tried to run the patch on the unedited src and it fails in the same way
Does Any one know how else to add the places section?

```
patching file main-menu/etc/slab.schemas.in.in
patching file main-menu/src/file-area-widget.c
Hunk #2 FAILED at 95.
Hunk #3 FAILED at 106.
Hunk #4 FAILED at 230.
Hunk #5 FAILED at 520.
Hunk #6 FAILED at 741.
Hunk #7 succeeded at 768 (offset -86 lines).
5 out of 7 hunks FAILED -- saving rejects to file main-menu/src/file-area-widget.c.rej

```

---

### Post by Twiggy794 on 2007-01-26
Best way to do this is to grab the source deb with ```
$ sudo apt-get source gnome-main-menu
``` then try tweaking that.  It'll have the patch that you want.

---

