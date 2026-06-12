---
title: "Unable to locate package lubuntu-dekstop / xubuntu-desktop"
date: 2015-09-19
forum: General Help
---

### Post by anonprophet on 2015-09-19
i want to install lubuntu-desktop or xubuntu-desktop but i get error
```
Unable to locate package lubuntu-desktop
```

already try 
```
apt-get clean
apt-get update
apt-get upgrade
```

but the problem still same

---

### Post by Bucky Ball on 2015-09-19
*Thread moved to **General Help**.*

What command are you attempting to install it with and why do you want to install the whole Lubuntu, which is what lubuntu-desktop will do? Not advisable. If you're installing that, just install Lubuntu or you are going to end up with bloat and redundancy (and possibly conflicts). 

If you just want the desktop environment used by Lubuntu, then:

```
sudo apt-get install lxde
```

Log out, choose lxde session from the Sessions menu, login.

---

### Post by anonprophet on 2015-09-19
thanks, im read guide from here

[http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/)

btw, im already install using ur command
but i just want to know, why my ubuntu cant locate package ?

---

### Post by Bucky Ball on 2015-09-19
Open Software Centre and search for 'lxde' or 'lubuntu-desktop'. Is it there and saying it is installed? Have you updated lately? You installed lxde using my command? Can you log out and log in to an lxde session?

---

### Post by anonprophet on 2015-09-19
yes, im already installed LXDE and can login with that environment

search in Software Center
lxde installed
lubuntu-desktop no items match

---

### Post by Bucky Ball on 2015-09-19
Hmm. That is odd. What are we missing? I just had a look in Synaptics (using same repos, of course) and there it is. 

What release are you using of Ubuntu?

---

### Post by anonprophet on 2015-09-19
im just downloading from ubuntu website
and freshinstall using Ubuntu 14.04.3 64bit

---

