---
title: "remove ask for root rights"
date: 2008-03-05
forum: General Help
---

### Post by System Monitor on 2008-03-05
When i install software, ubuntu asks for root privliges, i am the only system user and it gets annoying for me to need to type my password just to install a program, how can i stop it from asking?

I have Hardy

---

### Post by peitschie on 2008-03-06
As far as I know there isn't.

Possibly it might be worth reading this in case you haven't already: [https://help.ubuntu.com/community/RootSudo#head-6cfb89699f99dbeee57c81c64945454d6ded2fac](https://help.ubuntu.com/community/RootSudo#head-6cfb89699f99dbeee57c81c64945454d6ded2fac)

Basically, that is a "feature" that it is recommended to keep active.  The whole point is that a program needs to ask temporarily for elevated (root) privileges.  This gives you the opportunity to back out or to deny the program the ability to continue to install if you never intended it to do so.

While I understand the annoyance... how often do you install or uninstall applications?  Is the time saved really worth the security risks caused by automatically allowing an installer to access any part of the system?

---

### Post by tubasoldier on 2008-03-06
The only real way to do that is to run your system as root. But that is VERY TERRIBLE way to run your system. It is much easier to make an oops as root, let alone the security vulnerability you will create. I highly recommend against doing something like that.

When you first start using linux you will spend lots of time configuring, trying new software, ect... At first it seems like a lot, but after some time you will not type it very often because you will find yourself just using your system and not tweaking it.

Although I'm not a fan of weak passwords, if it is that big of an issue and you think your personal data on your computer is of no consequence then you could set an easier password. I don't really recommend that either but it may lighten your password load.

---

### Post by TigerWolf on 2008-03-06
If you are installing lots of things in the command line - you can do 
```
sudo su
```
might help

---

