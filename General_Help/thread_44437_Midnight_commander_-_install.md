---
title: "Midnight commander - install"
date: 2005-06-26
forum: General Help
---

### Post by 0tk on 2005-06-26
HI,
I' trying to install midnight commander. I'm still very new to Ubuntu.  I ran sudo apt-get update..

now what is next?
sudo apt-get install ? - what package name should i use here please?

---

### Post by adwait on 2005-06-26
try "apt-get install mc" as root.

---

### Post by az on 2005-06-26
Use synaptic to install stuff.  You can use aptitude,too, if you are in text mode.

Mc is in universe.

---

### Post by atomikku on 2005-06-26
i've tried to install midnight commander using apt-get
this is the output i had:
```
placid@d-ngn:~$ sudo apt-get install mc
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mc
```
maybe i have to install it form some binaries?

---

### Post by tristan on 2005-06-26
atomikku you need to make sure you have the various ubuntu repositories enabled. Have a look at the ubuntuguide [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) for how to do this, and for a lot of excellent ubuntu newbie tips as well :).

---

