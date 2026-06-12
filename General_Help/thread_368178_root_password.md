---
title: "root password?"
date: 2007-02-23
forum: General Help
---

### Post by hippieh8er15 on 2007-02-23
Im trying to switch users to root from the console i type su root and it prompts me for a password then i enter my password and it says authentication failure how do i fix that?

---

### Post by aysiu on 2007-02-23
You don't need to switch to root.

If you want to, though, just do ```
sudo -s
``` Most commands use *sudo*, though.

More details here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

