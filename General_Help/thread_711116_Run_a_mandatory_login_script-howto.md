---
title: "Run a mandatory login script-howto"
date: 2008-02-29
forum: General Help
---

### Post by kish on 2008-02-29
hi,

I wanted the login information(user, timestamp) to be sent to a server

I edited /etc/profile and added a line pointing to a script that takes care of that. 

Was wondering if that was the right way to do it
as I thought that users have their own login preferences that can override the default.

Any help would be greatly appreciated.

Thnx :-)

---

### Post by pointone on 2008-02-29
Users can have their own /home/username/.profile file, but I don't think it overwrites the system-wide /etc/profile; only supplements it.

---

