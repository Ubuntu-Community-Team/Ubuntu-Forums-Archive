---
title: "Where is the 'locate' database located?"
date: 2007-08-23
forum: General Help
---

### Post by oldcpu on 2007-08-23
The locate tool indexes files into a database.  I would like to know where the database is stored.

---

### Post by imbjr on 2007-08-23
Try looking in:
/var/lib/slocate

You'll probably have to sudo into it as its got some tight permissions.

---

### Post by oldcpu on 2007-08-23
No such folder.

---

### Post by jamvegan on 2007-08-24
That's where it is for me:
```
/var/lib/slocate/slocate.db
```

---

### Post by oldcpu on 2007-08-24
Anyway I can find out where mine is located?

---

### Post by jamvegan on 2007-08-24
```
sudo locate slocate.db
```

That finds mine.  If you're running Feisty, I can't imagine why it would not be in /var/lib/slocate/, though.  Is it possible that your system has not yet been indexed?  If so, you can index it by running:
```
sudo updatedb
```

---

### Post by oldcpu on 2007-08-25
Still nothing.

But I can hear by HDD working hard when I updatedb.

---

