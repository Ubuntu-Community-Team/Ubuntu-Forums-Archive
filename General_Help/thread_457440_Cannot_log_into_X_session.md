---
title: "Cannot log into X session"
date: 2007-05-28
forum: General Help
---

### Post by cknoblock on 2007-05-28
Hello all,

I can't seem to log into a X session using Feisty. This was working fine for weeks, and suddenly now it does not work. I get the following error in a message window when I try to login.

** ERROR ** Cannot find a safe socket path in '/tmp'
aborting...

Any help is appreciated.

Thanks!

-Chris

---

### Post by fdrake on 2007-05-28
can you log-in in safe mode gnome or terminal mode?or just press ctrl+alt+f1 to login in console and type :
less ~/.xsession-errors
post here some of the results if u can

---

### Post by cknoblock on 2007-05-28
Thank you for responding. Attached is the text dump you asked for. I cannot open a failsafe gnome session, only failsafe terminal.

-chris

---

### Post by fdrake on 2007-05-28
the problem (from what i understand) is caused from missing or unaccessible files that GConf uses. i'm not very familiar with this application, so i check the website, but to tell u the true i am still confused, my guess is that this application interacting with gnome and other graphical application won't let u login. my advise is to try remove or reconfigure the program. how did u install it, using the repos.?

---

