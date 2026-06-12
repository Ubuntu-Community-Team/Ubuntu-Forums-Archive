---
title: "Linux CMDs stored?"
date: 2008-03-27
forum: General Help
---

### Post by matt12345678 on 2008-03-27
Simple question: Where are the Linux commands stored? For instance when i type clear, ifconfig, ls, pwd, etc. where (directory path) in the system does it know to how to handle that command?

---

### Post by milton1 on 2008-03-27
many of these are in /usr/bin. However, any directory stored in your $PATH variable will be checked for the appropriate commend when one is called. I believe this variable is set in ~/.profile or /etc/profile, depending of the desired user scope.

---

### Post by p_quarles on 2008-03-27
Thread moved to General Help.

---

### Post by phrawzty on 2008-03-27
> **milton1 said:**
> many of these are in /usr/bin. However, any directory stored in your $PATH variable will be checked for the appropriate commend when one is called. I believe this variable is set in ~/.profile or /etc/profile, depending of the desired user scope.

You can also see where a particular command is located by using the "which" tool :
```
$ which ls
/bin/ls

$ which which
/usr/bin/which
```

---

### Post by matt12345678 on 2008-03-27
Thanks guys! You've been very helpful and I found exactly what I needed.

Love Linux.

---

