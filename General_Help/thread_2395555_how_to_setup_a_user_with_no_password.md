---
title: "how to setup a user with no password ?"
date: 2018-07-03
forum: General Help
---

### Post by anewbie on 2018-07-03
Is there a simple way to setup a user with no password. I'm trying to migrate someone from windows who is very old and can't handle a password (even a simple one).  THis user does not have admin privs. I did a bit of searching and couldn't find anything simple that worked - the old methods of editing shadow file and setting to :: (blank) didn't work.

---

### Post by steeldriver on 2018-07-03
Assuming they don't need to login via a CLI virtual console, you should be able give the ability to log in at the GUI without a password by adding the user to group `nopasswdlogin`

Their actual account should have a normal password regardless

---

