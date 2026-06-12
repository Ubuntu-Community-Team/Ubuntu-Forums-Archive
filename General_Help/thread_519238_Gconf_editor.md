---
title: "Gconf editor"
date: 2007-08-06
forum: General Help
---

### Post by sefs on 2007-08-06
How is it possible to delete an entire tree section from the gconf editor, as well as values etc.

---

### Post by distroman on 2007-08-06
I think this is what you might need-
```
gconftool-2 --recursive-unset /path/path
``` 
Also have a look at-
```
man gconftool-2
```

---

