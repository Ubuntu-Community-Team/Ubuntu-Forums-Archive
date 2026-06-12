---
title: "limited user permissions"
date: 2007-12-26
forum: General Help
---

### Post by Matthijs on 2007-12-26
i'd like to make a user with limited abilities. The user may not have the permission to list / and other directory's except his own /home dir. Do i need to chmod everything?

Matthijs

---

### Post by TidusBlade on 2007-12-26
I would think that you need to chmod everything, or maybe create a group and modify it's permissions, haven't really touched the user management section so just look around.

---

### Post by p_quarles on 2007-12-26
If you chmod everything, you will break your installation. Plus, this user will need access to parts of the root filesystem just for basic functionality. If you were to make /bin inaccessible to this user, for instance, the user wouldn't be able to use the ls command for anything.

Decide what you specifically want to hide, and make sure that those directories can't be "executed" by "others." The permissions would be either:
```
rwxrwxr--
```
or in octal:
```
774
```
You might also want to look into creating a chroot environment for this user. That would be a quicker way of accomplishing the privilege separation you're looking for.

---

### Post by bodhi.zazen on 2007-12-26
> **p_quarles said:**
> If you chmod everything, you will break your installation. Plus, this user will need access to parts of the root filesystem just for basic functionality. If you were to make /bin inaccessible to this user, for instance, the user wouldn't be able to use the ls command for anything.

Decide what you specifically want to hide, and make sure that those directories can't be "executed" by "others." The permissions would be either:
```
rwxrwxr--
```
or in octal:
```
774
```
You might also want to look into creating a chroot environment for this user. That would be a quicker way of accomplishing the privilege separation you're looking for.

+1

---

### Post by Matthijs on 2007-12-27
Alright, I'll check that out. Thank you very much.

---

