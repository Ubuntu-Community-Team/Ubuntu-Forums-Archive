---
title: "BMPx library too big"
date: 2007-05-21
forum: General Help
---

### Post by CocoAUS on 2007-05-21
BMPx apparently couldn't handle importing all my music and froze trying to, and now every time I restart it, it tries to load the library and crashes.

This problem continues even after I use aptitude purge and reinstall.  How can I keep this from happening?

---

### Post by duffman25 on 2007-05-22
> **CocoAUS said:**
> BMPx apparently couldn't handle importing all my music and froze trying to, and now every time I restart it, it tries to load the library and crashes.

This problem continues even after I use aptitude purge and reinstall.  How can I keep this from happening?

I think bmpx stores it's setting in .local/bmpx
Try to remove (or better move to another location) that directory.

Hope it helps.

---

### Post by CocoAUS on 2007-05-23
That did indeed help.  Thanks much.  Now the problem is getting it to load audio folder without crashing.

---

