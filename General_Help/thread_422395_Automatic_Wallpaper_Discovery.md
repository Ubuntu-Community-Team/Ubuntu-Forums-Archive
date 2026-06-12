---
title: "Automatic Wallpaper Discovery?"
date: 2007-04-25
forum: General Help
---

### Post by Zikes on 2007-04-25
I'd like to be able to add wallpapers to a certain directory and have Ubuntu automatically list them in its Desktop Background Preferences dialog.  Does Ubuntu use a directory for this?

---

### Post by Zikes on 2007-04-25
Apologies, a bit more time on google turned up an answer.  There's a ~/.gnome2/backgrounds.xml file that stores a list of backgrounds that appear in the Desktop Background Preferences dialog.

---

### Post by mskadu on 2007-04-25
And? Does this get updated whenever you add files to that directory?

---

### Post by Zikes on 2007-04-25
There actually isn't a directory, at least not that I've found.  The XML file stores an entry for a few default Ubuntu wallpapers, and then as you add more via the Desktop Background Preferences dialog they are added to that XML file.  The wallpapers you add are not moved to another directory, but must remain where they are for the XML file to stay accurate.

---

