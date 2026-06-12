---
title: "sudo root"
date: 2014-06-15
forum: General Help
---

### Post by Pedroski55 on 2014-06-15
Just out of interest: is there anything sudo can't do that root could do in Ubuntu? Is it possible to become root in Ubuntu?

Older versions of Linux used to ask for a root password on install, but that seems to have stopped.

---

### Post by Bucky Ball on 2014-06-15
Can't answer the first part, but it is possible to become root in a terminal with:

```
sudo su
```

Best to avoid, though. 

As far as I know you've only ever had to nominate a username and password at install. That hasn't changed.

---

### Post by grahammechanical on 2014-06-15
> **Enabling the Root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo.**

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by yancek on 2014-06-15
> Older versions of Linux used to ask for a root password on install, but that seems to have stopped. 		

Not really.  It may seem like it to Ubuntu users but, most 'distributions' still require a root user.  It is primarily Ubuntu and derivatives that don't require it and use sudo.

---

### Post by Pedroski55 on 2014-06-15
I also use Fedora. On install, it used to ask for a root password. Nowadays it only asks for a user password. Can't remember when that changed. Don't know if other distros still do

---

### Post by CharlesA on 2014-06-15
Depends on what distro tbh. IIRC, you can leave the root password blank in Fedora and it'll install sudo. Haven't checked in a while tho.

Also:

```
sudo -i
```

Is the preferred method to get a root shell.

---

### Post by CharlesA on 2014-06-15
Depends on what distro tbh. IIRC, you can leave the root password blank in Fedora and it'll install sudo. Haven't checked in a while tho.

Also:

```
sudo -i
```

Is the preferred method to get a root shell.

---

