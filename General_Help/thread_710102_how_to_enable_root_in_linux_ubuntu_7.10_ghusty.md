---
title: "how to enable root in linux ubuntu 7.10 ghusty"
date: 2008-02-28
forum: General Help
---

### Post by taimur on 2008-02-28
hi
i have install ubuntu 7.10
i want to enable it's root when i login to root it says u don't have administrative rights to access it
can you tell me how to enable root access in ubuntu 7.10 ghusty

---

### Post by desper on 2008-02-28
```
$ sudo passwd root 
```
and set a password for your root
```
Enter new UNIX password: 
Retype new UNIX password: 
```

done.

---

### Post by kellemes on 2008-02-28
Don't forget to read the warnings..
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by netztier on 2008-02-28
> **taimur said:**
> hi
i have install ubuntu 7.10
i want to enable it's root when i login to root it says u don't have administrative rights to access it
can you tell me how to enable root access in ubuntu 7.10 ghusty

I wouldn't recommend doing that. In Ubuntu, the root user is locked-down with good reason. Using root to log in is discouraged. To perform administrative tasks, use the  **sudo <command>** approach instead:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

From where:
>      
**Enabling the root account**

 <!> Enabling the root account is neither supported nor necessary.
      Anything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent root login, use sudo -i. Logging in to X as root is most likely to cause very serious trouble. If you believe you need a root account to perform a certain action, please consult the official support channels first, to make sure there is not a better alternative.


At first, this seems odd and complicated - but I got used to it and I have come to like this way of working.

best regards

Marc

---

