---
title: "Need to delete preferences - where are they stored in file system ?"
date: 2014-11-02
forum: General Help
---

### Post by michael-piziak on 2014-11-02
I somehow corrupted my ZSNES preferences.  Tried to uninstall and reinstall with no luck.

Where are the preferences for a program stored.  I can delete them and the program will re-create them, right ?

---

### Post by Impavidus on 2014-11-02
I don't know about ZSNES, but typically user settings (what most people deal with most of the time) are stored in a hidden file or directory in the user's home directory, either in ~/.progname or ~/.config/progname. If you delete the file, most programs will simply create a new file with default settings. System wide settings would be removed when you purge (not simply uninstall) the program using the package manager, and recreated when installing the package again.

---

### Post by michael-piziak on 2014-11-02
Thanks so much!   That's exactly what cured the problem !

---

