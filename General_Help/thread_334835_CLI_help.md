---
title: "CLI help"
date: 2007-01-09
forum: General Help
---

### Post by HughJass on 2007-01-09
How do I use chown to change ownership of all subfiles in a Directory?

If I do this   #chown sandy /home/sandy/Documents      it changes the Documents folder but not the contents.
Thanks
Sandy

---

### Post by lotheac on 2007-01-09
```
chown -R sandy:sandy /home/sandy/Documents
```

Try 'man chown' to bring up the manual for chown and other commands respectively.

---

### Post by HughJass on 2007-01-09
Thanks

---

