---
title: "How do I log in as root???"
date: 2008-05-18
forum: General Help
---

### Post by neilevan814 on 2008-05-18
I know that is probably as basic as it gets...but when i did my install of ubuntu 8.04 it did not ask me for a root password or username...It did ask me for my username and password....I tried to move the thunderbird icon onto my desktop as was told that I was not a root user so permission denied.
Thanks, Neil:KS

---

### Post by perlluver on 2008-05-18
> **neilevan814 said:**
> I know that is probably as basic as it gets...but when i did my install of ubuntu 8.04 it did not ask me for a root password or username...It did ask me for my username and password....I tried to move the thunderbird icon onto my desktop as was told that I was not a root user so permission denied.
Thanks, Neil:KS

I don't believe you can log in as root, however you can type Alt+F2 and enter gksu nautilus and then you will have root over all folders.

---

### Post by aysiu on 2008-05-18
Read these two links:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by zerosoul13 on 2008-05-18
on ubuntu you don't require to have a root password setup on the beginning as other flavors do, the root user is creater but gets locked so no one can actually login as root for security reason. 

If you need to work as root open up a terminal and do a " su - " enter your password and then you will be working as root, if you need to make changes on graphic mode you can write nautilus and thats it's.

hope this information works

---

### Post by NightwishFan on 2008-05-18
Just run anything you need to do with root with sudo or gksudo.

---

### Post by Coplen on 2008-05-18
sudo -s works when in the terminal.

---

### Post by paintba||er on 2008-05-18
```
sudo passwd root
```

---

