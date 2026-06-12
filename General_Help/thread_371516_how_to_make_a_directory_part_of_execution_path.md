---
title: "how to make a directory part of execution path"
date: 2007-02-27
forum: General Help
---

### Post by Mateo on 2007-02-27
I want to make the directory /usr/bin/scripts part of the execution path.  I tried:

```
export PATH=$PATH:/usr/bin/scripts/
```

but it only seems to last until I close the terminal.

---

### Post by ~LoKe on 2007-02-27
Could you use a bash alias?

---

### Post by Mateo on 2007-02-27
how?

---

### Post by Mateo on 2007-02-27
never mind, I put it in /usr/local/bin instead

---

### Post by bodhi.zazen on 2007-02-27
FYI if you want to add a path, for example, add these lines to ~/.bashrc :

PATH=$PATH:/usr/bin/scripts/
export PATH

---

