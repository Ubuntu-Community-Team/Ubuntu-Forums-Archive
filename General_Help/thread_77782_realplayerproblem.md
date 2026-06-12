---
title: "realplayerproblem"
date: 2005-10-17
forum: General Help
---

### Post by joanverde on 2005-10-17
I have sound in all other applications but not in realplayer while playing streams, though on startup.

My driver by sound deafault is esd

---

### Post by hajk on 2005-10-18
You may try the following symlink:

$ sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

Hope it works.

---

