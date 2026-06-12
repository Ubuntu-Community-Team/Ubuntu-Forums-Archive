---
title: "why isnt Sudo and User passwords differeent&gt;?"
date: 2007-10-08
forum: General Help
---

### Post by skymera on 2007-10-08
they shuould be different.

to improve security and hard to hack.

atm, if your account is hacked from getting the password, its the same as sudo password.
so...sudo is fairly useless in that case.

but if it was like PCLinuxOS, it would be more safe.

if they crack your user pass but not root, all they can do is trash your home.
safe system!

can you make them different? user and root?

just a though i guess

---

### Post by leg on 2007-10-08
sudo is checking your password to see if you are permitted to use the command. I think thats how it works anyway. Your password is not the same as root password at all.

---

### Post by McNils on 2007-10-08
It can be done. Just set a root password and remove all users from the admin group (in that order).

---

### Post by kellemes on 2007-10-08
Some reading..
[http://xtermin.us/whysudo/]("http://xtermin.us/whysudo/")

---

### Post by thirddeep on 2007-10-08
The user and root password is different.  Actually, root has no password by default on Ubuntu.

If you wish, you could first create a root password with:
```
sudo passwd root
```
then remove your user from the sudo list.

Thd.

---

### Post by skymera on 2007-10-08
so to do sudo

i use the roots password?

but will root be able to log in? i dont want it too.

thanks for ideas :)

---

### Post by ajgreeny on 2007-10-08
PLEASE, PLEASE, let's not go through this whole argument again.  The question has been discussed and answered so many times before it gets totally boring.

Do a search on this forum and you will find a lot of info on this.

---

### Post by por100pre1 on 2007-10-08
Sudo is a program to make your user account to fake root, not to become root. That's why it uses your password instead of root's password. Don't waste your time setting up a password for root.

---

### Post by zvacet on 2007-10-08
Add new user without admin privileges and work with it.Exept of course when you want to install or uninstall and things like that.

[https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by RedSquirrel on 2007-10-08
More reading, including some FAQ... ;)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

