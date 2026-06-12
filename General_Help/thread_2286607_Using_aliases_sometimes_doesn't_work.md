---
title: "Using aliases sometimes doesn't work"
date: 2015-07-13
forum: General Help
---

### Post by peter1897 on 2015-07-13
I have alias for **aptitude** which is **a**. But when i type **sudo a update** i get **sudo: a: command not found**. Why i am getting this error?

---

### Post by sudodus on 2015-07-13
Aliases work only when called directly from the command line, not as a parameter in a call to another program, so

```
a
``` works but not ```
sudo a
```

Since you should always run aptitude with elevated permissions, you can change the alias to contain sudo:

```
alias a='sudo aptitude'
```

---

