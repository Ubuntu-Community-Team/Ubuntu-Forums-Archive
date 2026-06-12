---
title: "yum equivelent in Ubuntu"
date: 2007-10-21
forum: General Help
---

### Post by robert scott on 2007-10-21
Hello all

sorry for such a dopey question ....

what is the Ubuntu equivelent for yum ? to update or install from a terminal window?

---

### Post by dmacdonald111 on 2007-10-21
You will need to use apt-get

ex:

sudo apt-get install <software>
sudo apt-get upgrade
sudo apt-get dist-upgrade

etc.

---

### Post by earobinson on 2007-10-21
aptitude >= apt-get

---

### Post by robert scott on 2007-10-21
Thank you 

Much appreciated ...

---

### Post by Maestro23 on 2007-10-21
> **robert scott said:**
> Thank you 

Much appreciated ...

Aptitude vs. Apt-get: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by por100pre1 on 2007-10-21
Some good reading:

```
man apt-get
```

```
man aptitude
```

```
man dpkg
```

For fun:

```
apt-get moo
```

---

