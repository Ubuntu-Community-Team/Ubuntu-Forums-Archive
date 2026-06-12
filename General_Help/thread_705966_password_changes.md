---
title: "password changes"
date: 2008-02-23
forum: General Help
---

### Post by intrexgrp on 2008-02-23
I have installed ubuntu  and have no idea what my root password is. My user password will not let me install or change any thing. is there any way to reset the root password to one I know ???

---

### Post by taurus on 2008-02-23
Did you actually assign a password for root?  Don't confuse root password with the password that you created when you first installed it.  That should be your login password with whatever you login name is.  However, if you use the same account that you created during the installing process, then you have a root privilege to run almost everything with sudo/gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by 1467 on 2008-02-23
if this is the user u maked at install u can go to system> admin > users and groups and click on the root user and click properties an change it from their.

---

### Post by 1467 on 2008-02-24
for user [COLOR="Blue"][http://http://www.brunolinux.com/01-First_Things_To_Know/Lost_User_Password.html]("http://www.brunolinux.com/01-First_Things_To_Know/Lost_User_Password.html")[/COLOR]
for root [COLOR="Blue"][http://www.brunolinux.com/01-First_Things_To_Know/Lost_Root_Password.html]("http://www.brunolinux.com/01-First_Things_To_Know/Lost_Root_Password.html")[/COLOR]

---

