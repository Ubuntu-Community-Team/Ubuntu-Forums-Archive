---
title: "messed up synaptic"
date: 2007-12-03
forum: General Help
---

### Post by billgoldberg on 2007-12-03
I screwed up synaptic. I force quitted it (sudo pkill synaptic) because it seemed to be stuck trying to download sun java 6 doc file along with some other java 6 files.

Now i can't downloadig anything.

An error pops up saying:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

I tried running dpkg --configure -a, but it just displays a list, and i'm stuck.

Could anyone help me?

---

### Post by forestpixie on 2007-12-03
did you do it with sudo 

```
sudo dpkg --configure -a
```

can you do it again and post the whole error message here

---

### Post by rsambuca on 2007-12-03
Run this```
sudo dpkg --configure -a
```

---

