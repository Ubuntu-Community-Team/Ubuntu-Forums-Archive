---
title: "[SOLVED] Bulk CVS Element Removal"
date: 2008-03-30
forum: General Help
---

### Post by cmnorton on 2008-03-30
I have the need to remove binary files in bulk from a CVS archive. If I remove the ",v" files, what else do I need to edit?

---

### Post by cmnorton on 2008-03-31
This can be done by editing a directory in the repository an CVS/Entries locally.
Remove the entry in CVS Entries, after making a backup copy. In CVSROOT on the server side, removing the corresponding ,v file completes the removal process.

---

