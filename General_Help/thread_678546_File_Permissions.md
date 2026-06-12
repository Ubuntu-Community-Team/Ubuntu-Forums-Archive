---
title: "File Permissions"
date: 2008-01-26
forum: General Help
---

### Post by th1bill on 2008-01-26
I typed mkdir /home/<user name>/dvd and the directory is there.  I cannot do anything with it and in superuser it tells me I do not own the file.  I goofed and I do not know how or what to do about it.

---

### Post by PeterJS on 2008-01-26
try:
```

sudo chown -R <user name>:<user name> ~/dvd

```

Chown is the program to change ownership, the first item is the owner name, the second one is the group it belongs to, by default all files you created owned by your user's personal group. So you might as well set that directory up the same way.

---

