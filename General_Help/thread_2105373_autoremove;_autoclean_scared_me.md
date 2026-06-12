---
title: "autoremove; autoclean scared me"
date: 2013-01-15
forum: General Help
---

### Post by alphaamanitin on 2013-01-15
Went to do the autoremove and autoclean and saw this > You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
Scared the absolute crap out of me, looks like it wanted to delete my x11 server.

AlphaA

---

### Post by zvacet on 2013-01-16
Run 

```
sudo apt-get update && sudo apt-get upgrade
```

You will see packages recommended for autoremove.if you don´t want them to be removed just install them again. ;)

---

