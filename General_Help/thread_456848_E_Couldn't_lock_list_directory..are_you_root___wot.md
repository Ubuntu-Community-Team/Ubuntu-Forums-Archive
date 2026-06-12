---
title: "E: Couldn't lock list directory..are you root?   wots this"
date: 2007-05-28
forum: General Help
---

### Post by ayush3090 on 2007-05-28
guys everytime i try to do anyything in the terminal.........like for updates and stuff....i get this error

E: Couldn't lock list directory..are you root?


???????

---

### Post by peterbrewer on 2007-05-28
You are trying to run a root(admin) task with only normal user privileges.  If you type sudo before the command it will temporarily change you to root for that one command. Please note it will ask you for the root password which is probably the same as your normal login password.

It is designed as a security measure to stop normal users damaging the system and to make sure that is what you want to do.

---

