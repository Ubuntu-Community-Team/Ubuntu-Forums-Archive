---
title: "root Q"
date: 2008-01-12
forum: General Help
---

### Post by Totallypclost on 2008-01-12
Hi,

O.K, i'm totally new to buntu, i've just been trying to install a program, everything has gone fine upto now, done the ./configure and make that's ok, i know you have to be root for the rest, so, i've done **su** and **sudo**,i've put in the only password i've got which is the one i put on the install, but i'm being refused entry,:confused:

> micheal@micheal-desktop:~/Desktop/FahMon-2.3.1$ su
Password: 
su: Authentication failure
Sorry.

Any ideas what i'm doing wrong, could you point me in the right direction?.

T.I.A

---

### Post by Muzer on 2008-01-12
Do ./configure
then make
then sudo make install .

---

### Post by Totallypclost on 2008-01-12
> **Muzer said:**
> Do ./configure
then make
then sudo make install .

Thanks Muzer, not use to that way of doing it, (su: root password) is the way i know, so the way you showed, is that the norm for buntu?.

---

### Post by geirha on 2008-01-12
> **Totallypclost said:**
> Thanks Muzer, not use to that way of doing it, (su: root password) is the way i know, so the way you showed, is that the norm for buntu?.

Yes, root doesn't have a password by default in ubuntu, but all users in the admin-group are allowed to run commands as root by putting sudo in front of the commands. Then it will ask for the user's password, and it will remember it for about 15 minutes. If you want a good old root-shell, you can run one of ```
sudo su
sudo bash
sudo -i
sudo -s
```
Read the man-page of sudo to see what the differences are

---

