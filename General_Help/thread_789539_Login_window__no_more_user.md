---
title: "Login window : no more user"
date: 2008-05-10
forum: General Help
---

### Post by X-dark on 2008-05-10
Hello,
I've just upgraded Ubuntu on my dad's computer (from 7.10 to 8.04 32 bit).
To log more easily I configured it to use Human list as login window. But since the update (or shortly after) there is no user appearing on the list. It's quite annoying. I can still log with typing the user name manually. Any idea ?

---

### Post by NilsE on 2008-05-10
This is a bug that was caused by the updates last night which has been logged.  The fix is in the entry but here it is.

In a terminal enter:

sudo /usr/sbin/add-shell /bin/bash

---

### Post by X-dark on 2008-05-10
Thank you

---

### Post by jdlittle25 on 2008-05-11
I had the same problem and this fixed it like a charm.  Thank you.

---

