---
title: "Problem with Sources Entry"
date: 2007-08-25
forum: General Help
---

### Post by cssutto on 2007-08-25
I keep getting erro messages:

[http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main packages ERROR subprocess gzip returned error code 1


Why?

---

### Post by jamvegan on 2007-08-25
This:
```
sudo rm /var/lib/apt/lists/partial/*
```
fixed the same problem for swy000 in [this thread]("http://ubuntuforums.org/showthread.php?t=532613&page=2").

---

### Post by cssutto on 2007-08-25
That did the trick!!

Thank you.

CSSJR

---

