---
title: "getting to root"
date: 2007-06-09
forum: General Help
---

### Post by Irti on 2007-06-09
ok this is like a dumb question...but how do i get to root in terminal

---

### Post by madmetal on 2007-06-09
> **Irti said:**
> ok this is like a dumb question...but how do i get to root in terminal

there are no dumb questions ;)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ikonia on 2007-06-09
If you have to ask that, it suggests you've not read much on using ubuntu. 

How a general browse at the links on ubuntu.com to for some general introduciton docs, you could end up breaking the system if your flying in and not reading the basic layout docs.

---

### Post by xthund3rh3adx on 2007-06-09
to get into a full root terminal, you need to set a password for root. 

sudo passwd root

enter a password

now in terminal, enter this:
su

then enter the password you just made.

you are now in  a full root terminal

---

### Post by init1 on 2007-06-09
> **xthund3rh3adx said:**
> to get into a full root terminal, you need to set a password for root. 

sudo passwd root

enter a password

now in terminal, enter this:
su

then enter the password you just made.

you are now in  a full root terminal
The other way is
```
sudo su
```

---

### Post by bettlebrox on 2007-06-09
> **init1 said:**
> The other way is
```
sudo su
```
Or
sudo bash

---

### Post by AnRa on 2007-06-09
Don't set the root password, just use "sudo -i"

---

