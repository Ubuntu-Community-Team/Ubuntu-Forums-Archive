---
title: "Change log on screen to allow entering username?"
date: 2013-04-24
forum: General Help
---

### Post by cableguy414 on 2013-04-24
I'm running Ubuntu 12.10.  The logon screen shows a list of usernames to select from.  How can I change this behavior to force the user to enter their username and not show a list?

Thanks.

Jason

---

### Post by nonamedotc on 2013-04-24
Try this - 

```

vim /etc/lightdm/lightdm.conf
greeter-hide-users=true

```

This *should* allow you to enter the username instead of selecting from a list. Hope this works! :D

---

### Post by CatKiller on 2013-04-24
Vim seems like quite a hardcore suggestion. Nano might be more new-user-friendly.

---

### Post by cableguy414 on 2013-04-25
First, I like VI.  Second, nonamedotc, your suggestion worked.

Thank you.

---

### Post by nonamedotc on 2013-04-25
Glad to hear that! Cheers! :)

---

