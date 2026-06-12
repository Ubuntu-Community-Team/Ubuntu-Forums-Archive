---
title: "Completely remove pidgin"
date: 2007-12-04
forum: General Help
---

### Post by nescontroller on 2007-12-04
I have a previously unresolved issue with pidgin. I was told that if I completely remove it and reinstall I should no longer have a problem. I have done apt-get remove --purge pidgin pidgin-data but when i reinstall all my preferences and screen names are still there. Is there anyway to completely purge all this data?

---

### Post by dbott67 on 2007-12-04
I believe Pidgin stores it's user settings in ~/.purple

So, if you delete, move or rename the .purple directory, it should take care of the problem.

-Dave

---

### Post by zvacet on 2007-12-04
**Home directory>view>show hidden files>.purple** Delete it.

---

### Post by weezalxc on 2007-12-04
Also, ./ or ."filename" means its a hidden file.  If you hit Ctrl+h, it will show hidden files.

---

### Post by nescontroller on 2007-12-04
Thank you!~

---

