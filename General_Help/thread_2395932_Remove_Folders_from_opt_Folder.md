---
title: "Remove Folders from opt Folder"
date: 2018-07-08
forum: General Help
---

### Post by bionic3epl on 2018-07-08
How do I remove folders from the opt folder?

---

### Post by TheFu on 2018-07-08
You can brute force remove them using **rm**, but that might break some package dependencies.  So, the best way is to remove any packages that were installed there using whichever tool you used to perform the installation.   Then, after you are 100% certain you removed all the related packages, you can use rm.

Whenever I do things like this, I want to relocate the files somewhere else to be certain it doesn't have anything bad as a side-effect.  Then run the computer for a week or two with the files "missing".  If nothing bad happens, then remove them.

Or was this really a question about rm and options for it?

---

