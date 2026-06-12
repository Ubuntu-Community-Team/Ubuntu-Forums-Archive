---
title: "Firefox loads automatically at login"
date: 2016-10-09
forum: General Help
---

### Post by ineuw on 2016-10-09
I am using Xubuntu 16.04 32bit with kernel 4.4.0.38 and every time I log in, Firefox 50.0b5 (beta) loads automatically. There is no entry for this in Session and Startup and I have no clue how to find the source. Can someone please clue me in how to find the source of this issue?

---

### Post by The Cog on 2016-10-09
Just a guess, but it worked for me once:

Close all your applications, then click the logout icon. At the popup where you can choose logout, shutdown or suspend, check the box to save session for future logins. Continue to log out, which will save the fact that you have no applications running. Log back in, and no applications should auto-start. Then log out straight away, unchecking the save session box in the process. Now when you log in, nothing should be started, and anything open when you log out will not be restarted next time.

---

### Post by bearlake on 2016-10-09
> **The Cog said:**
> Just a guess, but it worked for me once:

Close all your applications, then click the logout icon. At the popup where you can choose logout, shutdown or suspend, check the box to save session for future logins. Continue to log out, which will save the fact that you have no applications running. Log back in, and no applications should auto-start. Then log out straight away, unchecking the save session box in the process. Now when you log in, nothing should be started, and anything open when you log out will not be restarted next time.

Used this for the same reason as the OP before and it did the trick.

After everything was normal again I unchecked the box to save session for future login.

---

### Post by ineuw on 2016-10-09
The Cog, thanks. It worked. . . . . Bearlake, what is OP?

---

### Post by howefield on 2016-10-10
> **ineuw said:**
> ..... OP?

*Original Post* or *Original Poster,* ie, you :)

---

