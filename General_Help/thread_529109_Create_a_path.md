---
title: "Create a path"
date: 2007-08-18
forum: General Help
---

### Post by chejose on 2007-08-18
I am trying to Install a program, and am supposed to create a path to a folder. I have been searching trying to find out how to do it.... it must be simple! But so far don't see how to do it.
So thanks for the answer, and I will write it down for next time!!

José

---

### Post by taurus on 2007-08-18
You can edit ~/.bashrc

Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
and add the new path to it.

```
PATH=$PATH:/new_path
export PATH
```
Save it.  Then, either log out and back in again or source it.

```
source ~/.bashrc
```

---

### Post by chejose on 2007-08-18
Very good. Thanks. Sometimes it is possible to pass hours searching through different sites but not get a clear answer for a simple question like this one.
Printed it out, and will have it for next time!

José

---

