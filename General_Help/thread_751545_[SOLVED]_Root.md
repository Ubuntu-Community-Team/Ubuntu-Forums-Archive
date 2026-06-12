---
title: "[SOLVED] Root"
date: 2008-04-10
forum: General Help
---

### Post by littlepengiun00 on 2008-04-10
I have install Ubuntu 7.10 server edition and log in as root but I don't know the password for root.  When I install it, it does not ask me for a password for root; does anyone know if it have a default password for root during installation?  I create a user for me but with that user I can not do roots tasks.

Please advise!

---

### Post by ibutho on 2008-04-10
The root account is locked by default and everything you need to do as root can be done whilst logged in as a normal user. The first user created when you install Ubuntu is put in the admin group, so this user can run commands normally reserved for root by prefixing them with sudo e.g. "sudo nano somefile".

---

### Post by gunksta on 2008-04-10
ibutho beat me. . . . .

By default, Ubuntu doesn't use root. Ubuntu relies of sudo. When you installed and created your first user, this user was added to the list of users who are allowed to use sudo.

Thus, if you want to install a program called foo, you would need to type in:

```
sudo apt-get install foo
```sudo - let me do this like root!
apt-get - this is a command line program management tool
           install - a command for apt-get
           foo - the program we are installing

---

### Post by bodhi.zazen on 2008-04-10
To access a root shell use sudo

```
sudo -i
```

Use you user log in password ;)

---

### Post by aysiu on 2008-04-10
I'm surprised no one has linked to this yet: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by littlepengiun00 on 2008-04-11
Thanks all,

This help me alot!

---

