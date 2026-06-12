---
title: "Renaming Files"
date: 2006-11-09
forum: General Help
---

### Post by yellow beard on 2006-11-09
HI. Im trying to rename all files in a directory with the extension .ico to .xpm with the rename command but i cant get it to work. Can some one tell me how to do it?

---

### Post by bsussman on 2006-11-09
the syntax is:

```
bos@Dillon:~/junk$ rename 's/<current string>/<new string>/' <filestochange>
```

the man page for rename has examples

---

### Post by aysiu on 2006-11-09
Use KRename?

---

### Post by yellow beard on 2006-11-09
> **bsussman said:**
> the syntax is:

```
bos@Dillon:~/junk$ rename 's/<current string>/<new string>/' <filestochange>
```

the man page for rename has examples

Cheers that worked. I like using the terminal.

---

