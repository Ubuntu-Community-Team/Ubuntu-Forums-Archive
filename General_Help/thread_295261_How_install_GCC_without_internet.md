---
title: "How install GCC without internet?"
date: 2006-11-07
forum: General Help
---

### Post by Necreia on 2006-11-07
Hello.  I installed Dapper Drake 6.06 and don't have a working wireless driver.  In order to do that, I need to use gcc so I can 'make'.

However, the machine I need to do this on, doesn't have gcc.  How do I install it without the app-install command or whatnot?  I went over to gnu.gcc.org and looked at the install readme's, and got a little confused.  I see references to using "make" to build, but that's what I'm missing.

Is there a simple way to go about this?

Edit: I'm able to download whatever I need to on another machine, and transfer it over via CD.

---

### Post by CatKiller on 2006-11-07
**build-essential**, which contains gcc, is already on the install disk.

```
sudo aptitude install build-essential
``` should work, I think, although you'd possibly have to add the install disk as a repository.

---

### Post by Necreia on 2006-11-07
Thanks! I'll give that a try.

---

