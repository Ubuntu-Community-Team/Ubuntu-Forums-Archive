---
title: "[SOLVED] Safe to delete contents of /var/cache/apt/archives?"
date: 2008-05-28
forum: General Help
---

### Post by freymann on 2008-05-28
I notice I'm getting low on disk space and realize that update manager caches files it has been installing, and now I would like to remove them as they are no longer needed.

Therefore, can I delete all the files in

/var/cache/apt/archives

without breaking anything?

---

### Post by pointone on 2008-05-28
```
sudo apt-get clean
```

...instead.

---

