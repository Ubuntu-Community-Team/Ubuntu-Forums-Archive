---
title: "Remove root account?"
date: 2005-10-15
forum: General Help
---

### Post by veraction on 2005-10-15
OK, so i did a ```
sudo passwd root
``` cause it seemed as if I needed to for some program, and now I regret it.

How do I go about disabling this account again?

---

### Post by adwait on 2005-10-15
```
sudo passwd -l root 
```

---

### Post by veraction on 2005-10-15
Ok, thanks. looks like it'll work.

---

