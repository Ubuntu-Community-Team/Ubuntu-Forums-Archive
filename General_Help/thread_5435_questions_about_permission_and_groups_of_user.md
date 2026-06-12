---
title: "questions about permission and groups of user"
date: 2004-11-18
forum: General Help
---

### Post by kixvn on 2004-11-18
i installed some software using "su" mode, and it places a file in /etc/opt/...

i went to "user and groups" to add to my current home account (which is not "root") the group "root" and "user"

and for that file in /etc/opt/ .. i checked the permission, which is 755

but, when i logged in using my home account, i still can't execute that file, it said that i need super user access or things like that

can somebody help me with this ?

thanks :)

---

### Post by FLeiXiuS on 2004-11-18
[QUOTE=kixvn]i installed some software using "su" mode, and it places a file in /etc/opt/...

i went to "user and groups" to add to my current home account (which is not "root") the group "root" and "user"

and for that file in /etc/opt/ .. i checked the permission, which is 755

but, when i logged in using my home account, i still can't execute that file, it said that i need super user access or things like that

can somebody help me with this ?

thanks :)[/QUOTE]

Take a look at the man pages for CHOWN.

```
man chown

example: chown user.group -parameters /path/to/file
```

---

