---
title: "Map windows style absolute path to specific folder?"
date: 2008-07-09
forum: General Help
---

### Post by Guy Gizmo on 2008-07-09
I have an issue using a cross-platform Linux / Windows / Mac OS X program.  Basically, when working on projects, it oftentimes (even when told not to) saves paths to files as absolute pathnames, resulting in cannot-find-file errors when you try work in the other OSes.  Most of the work is being done in Windows, meaning that the paths often start with C:/ or Y:/ or something similar.

Is there anyway to teach Ubuntu (or possibly many flavors of *nix) to automatically recognize that a path starting with a drive letter, like C:/, should direct to a specific folder?  i.e. having the Windows-style path:
C:/some/directory/
be interpreted as:
/windowsData/some/directory/

I've already considered creating symbolic links named C: that lead to the right place, but unfortunately there's no guarantee what the working directory will be, so that's not really feasible.

Any help is appreciated!

---

### Post by Titan8990 on 2008-07-09
Where is your Windows partition currently mounted?

---

### Post by Guy Gizmo on 2008-07-09
> **Titan8990 said:**
> Where is your Windows partition currently mounted?

Actually I guess I should clarify that it's a bit more complicated than that.  It's not so much a Windows partition as it is the same network server mounted in both Linux and Windows.  In Windows, it's mounted to Y:/ using the "Map network drive" feature, and in Ubuntu it's automounted to /media/servername/

But basically, I'd want any filepaths like Y:/* to be directed to /media/servername/*

---

### Post by Guy Gizmo on 2008-07-09
bump - I still have no idea how to fix this

---

