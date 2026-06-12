---
title: "root account"
date: 2007-08-02
forum: General Help
---

### Post by reynji on 2007-08-02
I installed ubuntu 6 asked me to create user name I did! But when I go to super user it says
su authentication failure. What did I do wrong during install?!

---

### Post by Happy_Man on 2007-08-02
Did you type your password wrong?

---

### Post by ajgreeny on 2007-08-02
Ubuntu doesn't use **su** for superuser and by default there is no available root account.  Ubuntu and its derivatives all use **sudo** instead.  Have a look at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) which tells you everything.  Once you are used to it it just becomes as normal as breathing.

You can have a root user if you really must, but it's not recommended by the ubuntu people.  Do a search and you'll find out how to do it.

---

### Post by milosz.galazka on 2007-08-02
You can get root shell by using

sudo su

and typing your password

---

