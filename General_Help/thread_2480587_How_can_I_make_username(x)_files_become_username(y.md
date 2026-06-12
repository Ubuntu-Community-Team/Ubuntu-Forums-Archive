---
title: "How can I make username(x) files become username(y) files?"
date: 2022-11-03
forum: General Help
---

### Post by sofasurfer on 2022-11-03
My installations /home directory <username(x)> will be restored from backup to a different installation owned by <username(y)>. What proceedure is used to make this /home directory belong to <username(y)>? Is this simply a <chown> command?

---

### Post by The Cog on 2022-11-03
Yes.
```
sudo chown -R username:username /home/username
```
should do the trick.

---

