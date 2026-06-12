---
title: "File-Roller 2.11.1"
date: 2005-06-04
forum: General Help
---

### Post by SpEcIeS on 2005-06-04
A while ago I upgraded my ***file-roller to 2.11.1***  via Backports, but now I seem to be getting crashes when I create an archive in nautilus. I am not sure if this is in direct relation to file-roller, but the two seem to be related. The crash happens when compression completes, however the tarball will be there upon nautilus restart. Has anyone else experienced the same problem? 

If I want to return to the original file-roller that comes with **Ubuntu 5.04**, how would I go about this? When I attempted to remove this program to return to the previous version it wants to remove **Ubuntu desktop**. Perhaps I should remove it in terminal using dpkg. Any ideas how to fix, undo, this mess?  :???:

---

### Post by bored2k on 2005-06-04
[QUOTE=SpEcIeS]A while ago I upgraded my ***file-roller to 2.11.1***  via Backports, but now I seem to be getting crashes when I create an archive in nautilus. I am not sure if this is in direct relation to file-roller, but the two seem to be related. The crash happens when compression completes, however the tarball will be there upon nautilus restart. Has anyone else experienced the same problem? 

If I want to return to the original file-roller that comes with **Ubuntu 5.04**, how would I go about this? When I attempted to remove this program to return to the previous version it wants to remove **Ubuntu desktop**. Perhaps I should remove it in terminal using dpkg. Any ideas how to fix, undo, this mess?  :???:[/QUOTE]
 Open up synaptic package manager. Select file roller >  settings > force version > select hoary.

---

### Post by SpEcIeS on 2005-06-04
[QUOTE=bored2k]Open up synaptic package manager. Select file roller >  settings > force version > select hoary.[/QUOTE]
Thanks :) It was under "Package" in synaptic, however after changing the versions the same problem seems to be there. I guess it was not file-roller-2.11.1. Prior to this upgrade, I cannot remember this problem happening. Could be wrong though.  :roll:

---

### Post by SpEcIeS on 2005-06-12
Nautilus is still crashing, but it may not be due to the file-roller, in fact it is not. Now it would seem that when using configure, when compiling programs, it will crash. Basically it looks, to me, like when files are created in using another program the nautilus comes apart. 

Since there is no other complaints regarding this problem, I would assume that it is relative to my system installation, so what could be causing this issue? Perhaps there is a corrupted file, or something?

Any ideas?  :-?

---

