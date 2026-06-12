---
title: "Firefox"
date: 2008-03-20
forum: General Help
---

### Post by rw2007 on 2008-03-20
I installed firefox 3 on my laptop with gutsy gibbon and when I clicked on the firefox icon in the panel it says it couldn't open it.  so I installed firefox via mozilla.org  but I just want the firefox I got originally with gutsy gibbon.

---

### Post by NightwishFan on 2008-03-20
Reinstall it with synaptic I assume.
```
sudo apt-get purge firefox && sudo apt-get install firefox
```
You might have to delete the current firefox first, I advice this.

---

### Post by rw2007 on 2008-03-20
But how I do get back the default firefox I got when I installed Ubuntu?

---

### Post by doorknob60 on 2008-03-20
```
rm -rf ~/.mozilla
```

WARNING: That will erase all your bookmarks, history, etc.

---

