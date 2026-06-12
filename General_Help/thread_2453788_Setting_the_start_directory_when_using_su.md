---
title: "Setting the start directory when using su"
date: 2020-11-17
forum: General Help
---

### Post by NotQuiteSU on 2020-11-17
I have an account, AccountB, which does not permit SSH login. I can only access it by using su.

When I am in AccountA, I use sudo su to switch into AccountB. But the directory I am in when I su is whichever current directory, including AccountA's home directory.

Can I set up AccountB so when I su into it, it will go to a specific directory. Home or otherwise?

---

### Post by The Cog on 2020-11-17
```
su -l AccountB
```
simulates a login by AccountB, which amongst other setup, sets the working directory to the user's home.

---

