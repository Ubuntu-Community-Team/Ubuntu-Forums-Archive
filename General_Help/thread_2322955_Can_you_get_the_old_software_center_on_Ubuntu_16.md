---
title: "Can you get the old software center on Ubuntu 16?"
date: 2016-05-01
forum: General Help
---

### Post by lamda0shotgun on 2016-05-01
I really hate the new one, I don't see how it is any better, and I want to access my install history.

---

### Post by Frogs Hair on 2016-05-01
It is available in 16.04, but history will only begin when installed. 

```
sudo apt-get install software-center
```

---

### Post by vasa1 on 2016-05-01
> **lamda0shotgun said:**
> I really hate the new one, I don't see how it is any better, and I want to access my install history.
Hating things won't get you far ;)

Your install history for software registered with the system could be in
/var/log/apt/history.log
/var/log/apt/term.log
/var/log/dpkg.log

and in their archived versions.

---

