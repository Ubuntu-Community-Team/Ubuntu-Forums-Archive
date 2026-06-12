---
title: "How do you set the root user and password? (cant install java)"
date: 2005-08-12
forum: General Help
---

### Post by billy314159 on 2005-08-12
I can't sudo into root and im trying to install java , but i got the "permission denied" string. (once i made the ns7? link, or tried to)

---

### Post by amohanty on 2005-08-12
> I can't sudo into root 

Can you post what you typed into the terminal...

AM

---

### Post by Gefion on 2005-08-12
Scrap that...
Found an answer to this post elsewhere on the board

at your prompt do
[CODE]
foo@bar:~$ sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
foo@bar:~$
[CODE]

---

### Post by amohanty on 2005-08-12
Ok. heres the deal. The default ubuntu setup does not allow you to login to the root account. Instead you get to use sudo. The default user you setup is in the sudoers list and can do everything that root can, just that you have to provide _your_ password everytime.

If you really, really want to do an su:
>> sudo passwd

This will allow you to setup the root password and then you can login as su.

HTH
AM

---

### Post by mird on 2005-08-12
This should also give you a root shell:
```
sudo bash
```

---

