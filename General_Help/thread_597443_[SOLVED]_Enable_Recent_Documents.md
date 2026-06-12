---
title: "[SOLVED] Enable Recent Documents"
date: 2007-10-30
forum: General Help
---

### Post by werdna5225 on 2007-10-30
The other day I disabled the recent documents under the places menu.  I thought I would be able to change it back but I can't.  The code I used to change it is:  

sudo rm ~/.recently-used ~/.recently-used.xbel && mkdir ~/.recently-used.xbel

Does anyone know how to re-enable the Recent Documents?

---

### Post by ohzopants on 2007-10-31
Try this:
```
touch ~/.recently-used.xbel
```

This creates an empty file called .recently-used.xbel in your home directory.
This will not restore whatever your recent documents were before you disabled it, but it will keep track of whatever you open from now on.

---

