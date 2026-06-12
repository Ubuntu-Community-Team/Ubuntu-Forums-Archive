---
title: "Login loop bug"
date: 2007-02-26
forum: General Help
---

### Post by Milesowl on 2007-02-26
Hello everyone,

I have this problem with my ubuntu Edgy Eft version:

Everytime I enter my login/password, it starts loading (the HD makes noise...then I see a flash of beige, then a black screen...and then the login appears again... 

This happened after my Power Supply blew because of a power surge. Edgy was running when it happened so maybe some files are corrupted or something ?? 

Any help appreciated... otherwise I would need to reinstall I suppose :(

---

### Post by taurus on 2007-02-26
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, check your disk space with

```
df -h
```
or look at the X error message to see what's wrong with it.

```
tail -20 ~/.xsessions-errors
```

---

