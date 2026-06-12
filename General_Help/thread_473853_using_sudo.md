---
title: "using sudo"
date: 2007-06-14
forum: General Help
---

### Post by rpm13 on 2007-06-14
Say my login name is rpm13
I want sudo to execute its argument but not ask me for my password
My sudoers has
```

root    ALL=(ALL) ALL
rpm13 ALL=(ALL) ALL
rpm13  ALL = NOPASSWD: ALL

```
But it still asks for my password.

What am I doing wrong?

---

### Post by NeoLithium on 2007-06-14
Switch it to look like this:
```

root    ALL=(ALL) ALL
rpm13 ALL=(ALL) NOPASSWD: ALL

```

With both in there, it will continue to ask for a password, this way it will only find the nopassword option that you have set.

---

