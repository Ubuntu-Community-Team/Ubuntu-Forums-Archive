---
title: "'Root' user"
date: 2007-04-20
forum: General Help
---

### Post by Loki-uk on 2007-04-20
Hi can anyone tell me how to log into the real 'root' user account in ubuntu? I have enabled it but I can't login. If you try to login from the boot login screen it says that the root is not allowed to login from here? Where else would I log in?

Thanks

---

### Post by AAM on 2007-04-20
In ubuntu you use *sudo* not a root login.

I don't want to patronize you with instructions you already know, but in case you don't. when you undertake an administrator's action in the GUI, you will be asked for your password. If you don't want someone to be able to do this, take them off the 'admin' group in **Users & Groups** (after you have entered the root password! The root password is the password of anyone belonging to the Admin group.

If you want to start a program like gedit or nautilus as a root user, open a terminal and type
> sudo gedit /directory/filename
or
sudo nautilus

hope I have helped

---

### Post by daygoj on 2007-04-20
is any body steal here?, well if u just happen 2 iono read, could u tell me how to set azereus as my default torrent opener besides i dont wont stuff to open with that stupid bittorent thing????????????????????????????????????????????? ?????????????

---

### Post by Compyx on 2007-04-20
To enable the root account, do:
```
sudo -s
```
you'll then become root, then you'll need to set a root password since it's scrambled by default:
```
passwd
```

Normally you won't need the root account, so it's probably best to leave it disabled. Anything you need to can be done with sudo (the preferred method on Ubuntu).

---

### Post by Loki-uk on 2007-04-20
Thanks for that. I've only been using ubuntu a week and I know you need the sudo command but I have something that needs to use the 'root' user sudo doesn't work.

Thanks again for the help :)

---

### Post by dominicd on 2007-04-20
> **Loki-uk said:**
> Thanks for that. I've only been using ubuntu a week and I know you need the sudo command but I have something that needs to use the 'root' user sudo doesn't work.

Thanks again for the help :)

What do you need to do?

---

### Post by rich.bradshaw on 2007-04-20
sudo -i

gets you logged in "as root", i.e. everthing you type is prefixed with sudo..

If you need something to be run as root, just sudo it.

---

