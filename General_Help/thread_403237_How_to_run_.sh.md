---
title: "How to run .sh"
date: 2007-04-06
forum: General Help
---

### Post by StarLog on 2007-04-06
I have a file from a vendor that ends in .sh
How do I execute this file, what is needed, because it says: command not found

---

### Post by taurus on 2007-04-06
You need to be in the same directory where that file is.  Then, try to run it like

```
chmod 755 **filename.sh**
./**filename.sh**
```

---

### Post by StarLog on 2007-04-06
Thanks that worked...:)

---

