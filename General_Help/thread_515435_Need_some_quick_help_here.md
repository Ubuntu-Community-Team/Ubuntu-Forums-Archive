---
title: "Need some quick help here"
date: 2007-08-02
forum: General Help
---

### Post by popocus on 2007-08-02
i have been trying to log in as root but i cannot 
this is the message i get
desktop:~$ sudo -i
sudo: must be setuid root
desktop:~$ sudo -s
sudo: must be setuid root
-desktop:~$ su
Password: 
su: Authentication failure
Sorry.
-desktop:~$ 

im kinda neww to this so any help would be greatly appreciated thank you.

---

### Post by aragorn2909 on 2007-08-02
Have you done this?

```
sudo passwd root
```

---

### Post by Terry of Astoria on 2007-08-02
You're supposed to sudo everything instead of logging in as root. Many people do though. Just be careful I think you have to make a password for root before it'll work. If you really need to do it, you can but it's not recommended usually. To do root commands using sudo simply prepend sudo to the command, eg:
```
sudo apt-get install xaos
```
To set a root password, just 
```
sudo passwd root
```
But don't blame me if you forget to log out of a root termional and your cat walks on the keyboard, and deletes your term paper.

---

### Post by dragonwings on 2007-08-02
sudo su

or  if ya want to copy/delete/mess around with filesystem / folders etc
sudo nautilus

---

