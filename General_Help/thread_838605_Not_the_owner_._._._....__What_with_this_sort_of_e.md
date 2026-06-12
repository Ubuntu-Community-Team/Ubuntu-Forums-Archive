---
title: "Not the owner . . . ....?  What with this sort of error?"
date: 2008-06-23
forum: General Help
---

### Post by thrasher6900 on 2008-06-23
I try to run some programs through wine and it says that I'm not the owner and it kills the process.

I've even made myself root user and tried to run the app and it still gave me the same non owner error.

Why am I 'not the owner' of some of my programs

---

### Post by Rocket2DMn on 2008-06-23
Try running
```
sudo chown -R <yourusername>:<yourusername> ~/.wine
```
That will set ownership of the .wine directory to your username (substitute in your username of course, no <> either).

---

