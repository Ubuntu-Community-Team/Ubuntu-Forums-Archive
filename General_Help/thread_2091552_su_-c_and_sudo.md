---
title: "su -c and sudo"
date: 2012-12-05
forum: General Help
---

### Post by sunveer on 2012-12-05
su -c command allows one to enter only single command like sudo without entirely logging to root.

So, is su -c equivalent to sudo in security or still I must use sudo?

---

### Post by AstroLlama on 2012-12-05
logging into the root account is never 100% "secure". 

for your own personal machine it probably won't make too much difference, but worked into a program "sudo" is probably a better choice.

Every user who wants to use the "su" command must know the root password (not set by default on fresh install). Multiple users who want to use the "su" command would have to know the root password, this is not secure. Just use sudo, it's easier that way and you will only have to remember 1 password, not 2. 

"sudo" let's you run a command as an admin (if you have the priviliges to run admin commands) and the password is the user password, unique for each person. If you're dealing with multiple users add them to the list of users with sudo priviliges, but never give away the root password!

---

### Post by rnerwein on 2012-12-05
> **sunveer said:**
> su -c command allows one to enter only single command like sudo without entirely logging to root.

So, is su -c equivalent to sudo in security or still I must use sudo?
try:
1. sudo /bin/bash
# env > blu
# exit
su
pa.....
# env > bla
# exit
$ diff -y blu bla
this can result in problems wich are hard to find.

---

