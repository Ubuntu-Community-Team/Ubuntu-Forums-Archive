---
title: "how to become root?"
date: 2007-05-03
forum: General Help
---

### Post by adi-n on 2007-05-03
hey, im a linux newbie...
how can i become root in the console?
i type su and then my password but i get:


su: Authentication failure
Sorry.


why?

---

### Post by taurus on 2007-05-03
You don't become root.  You use sudo if you need to run something as root.

```
sudo **command**
```


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by adi-n on 2007-05-03
thanks!
anyway why wrong password when i try to use the su command?

---

### Post by CocoAUS on 2007-05-03
The password error is because su means to switch users.  sudo is the command for the current user's super-user powers.  So when you use sudo, you stay the current user, and it asks for the current user's password.  When you use su, you are switching to root (or another user), and so you need that user's password.  By default, Ubuntu does not have a root user password.  It's not suggested that you use one since logging in as root is dangerous, and you can perform all the same actions using sudo anyway.

---

### Post by atlien on 2007-05-07
So what if you need to do something like add to or modify a file in /  ?
How do you log in as root and do that?

---

### Post by taurus on 2007-05-07
```
gksudo gedit /path_to_file
```

---

