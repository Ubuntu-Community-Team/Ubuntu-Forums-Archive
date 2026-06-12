---
title: "Mount NTFS in read/write mode"
date: 2005-08-03
forum: General Help
---

### Post by xodeus on 2005-08-03
See topic. Is it possible. If yes how? Anyone succeed?

---

### Post by heimo on 2005-08-03
Not possible with Ubuntu default kernel (or any precompiled Ubuntu kernel, AFAIK). So, yes - it's possible, and considered experimental and dangareous for your data. How? Compile kernel with NTFS write support.

---

### Post by foxy123 on 2005-08-03
[QUOTE=xodeus]See topic. Is it possible. If yes how? Anyone succeed?[/QUOTE]
I saw a HOWTO about captive driver which allows read/write for NTFS. Never tried/needed though on Ubuntu. You may search for 'captive' in HOWTOs.

I would not recommend enabling kernel suport since it is still (and I guess will be) unstable.

There is also a commecial driver, but I do not remember its name (something starting with 'p' I think).

---

