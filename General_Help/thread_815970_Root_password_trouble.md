---
title: "Root password trouble"
date: 2008-06-02
forum: General Help
---

### Post by CelticShamrock on 2008-06-02
I'm a new user and I'm trying to install several programs into my Ubuntu. I open terminal type su and it asks for the root password, I do not remember setting a root password, and if I had it would be my normal password that I've typed in. How do I find out my root password?

---

### Post by geirha on 2008-06-02
You don't have a root password in ubuntu, you use sudo (with your user's password) instead. Use ```
sudo command to be run as root
``` to run a single command as root, and ```
sudo -i
``` to get a root shell, like with ```
su -
```

More info at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by pmlxuser on 2008-06-02
> **CelticShamrock said:**
> I'm a new user and I'm trying to install several programs into my Ubuntu. I open terminal type su and it asks for the root password, I do not remember setting a root password, and if I had it would be my normal password that I've typed in. How do I find out my root password?


anyway when you install ubuntu, the first user has the root previlages of course you don't log in as root.

You just give that user the root previlages using  the "sudo" comand

ie

$ sudo -options- command

when required to supply the root password -you type the password that you logged in with (specifically if you were the first user / if you were added to the system in the with root previlages.

---

