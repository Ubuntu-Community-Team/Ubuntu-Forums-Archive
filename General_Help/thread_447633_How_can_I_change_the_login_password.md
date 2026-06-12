---
title: "How can I change the login password?"
date: 2007-05-18
forum: General Help
---

### Post by knadoor on 2007-05-18
title. Just want to know, when you first log into ubuntu and type in your user name and password. Well how to change this password??

thanks :)

---

### Post by taurus on 2007-05-18
Are you able to log in at all?  If yes, then you can change to a new password with

Applications -> Accessories -> Terminal
```
passwd
```
But if you have forgotten your password, then you need to boot into recovery mode from GRUB menu and change it with

```
passwd knadoor
```
_assuming_ knadoor is your login name.

---

