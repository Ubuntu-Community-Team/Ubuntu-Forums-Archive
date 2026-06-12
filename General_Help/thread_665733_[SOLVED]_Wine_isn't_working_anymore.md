---
title: "[SOLVED] Wine isn't working anymore"
date: 2008-01-12
forum: General Help
---

### Post by omglol741 on 2008-01-12
I uninstalled Wine because I thought it was messing something up, but it was something else. So I installed it again, but now it can't make a C drive. I try to autodetect in the configure wine thing and it won't make one. It doesn't save it either when I hit apply, so when I go back all the other drives are gone too. I tried making a folder called Drive C and putting in the path to that but it doesn't work either. I think I deleted the .wine folder when I uninstalled it. How do I get that back? It says that folder already exists when I try to make it, but it's invisible so I can't even open it.

---

### Post by b0rka7a on 2008-01-12
Delete the folder .wine and type in a terminal:
```
wineprefixcreate
```

Edit: If you want you can rename it only, without deleting it.
you can see it by going to your home dir and pressing Ctrl+H

---

### Post by omglol741 on 2008-01-12
OK, that worked. Thanks a lot!

---

### Post by b0rka7a on 2008-01-12
You're welcome ;)

---

