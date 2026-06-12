---
title: "libcairo2 not authenticated in update manager"
date: 2007-12-15
forum: General Help
---

### Post by Lary Grant on 2007-12-15
I get "NOT AUTHENTICATED" for libcairo2 in update manager.

---

### Post by rsambuca on 2007-12-15
Sounds like you need to add the GPG keys for the ubuntu repos.

---

### Post by Lary Grant on 2007-12-15
> **rsambuca said:**
> Sounds like you need to add the GPG keys for the ubuntu repos.
That doesn't seem right... I've had ubuntu on this machine for a while and had several updates without this problem.

How could I check if I have the keys... something with apt-keys?

---

### Post by rsambuca on 2007-12-16
Try this first, just to see if everything is working```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Lary Grant on 2007-12-16
That seemed to update it with no problems.

---

