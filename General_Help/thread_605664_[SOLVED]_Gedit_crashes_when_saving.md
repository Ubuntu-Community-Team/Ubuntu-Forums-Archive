---
title: "[SOLVED] Gedit crashes when saving"
date: 2007-11-07
forum: General Help
---

### Post by Tampio on 2007-11-07
Yesterday morning gedit worked just fine, I had one document open the whole day, and when later I clicked "save", gedit just closed down. During the day I only installed qt3-qtconfig and qt4-qtconfig and the required dependencies, which I now have uninstalled, but as would be expected, they didn't affect the problems in any way.
When I run gedit from the terminal it says after crashing "Segmentation fault (core dumped)". You would think problems like this don't appear out of nowhere, but I can't think of anything I did that could cause this.


Edit: more testing revealed that gedit crashes when going to open or save window, as does OpenOffice. And gThumb doesn't start at all, it gives the same segmentation fault. So it seems the problem is in Gnome's file browser dialog or whatever the correct terms are? Opening files on GIMP or Gnome Subtitles works fine though.

Edit2: Problem solved. Note to self: do not hit tab in front of every line in .gtk-bookmarks, in an effort to remove those shortcuts from "places".

---

