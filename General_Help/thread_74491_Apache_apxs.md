---
title: "Apache apxs"
date: 2005-10-11
forum: General Help
---

### Post by dbee on 2005-10-11
I can't seem to get the apxs or apxs command in apache2 to work ... all I get is a 'command not found'.

I have mod.so compiled into apache, I also have the libapache2 perl module in their .... yet all I seem to get is 'command not found' 

any suggestions ?

---

### Post by dbee on 2005-10-11
It seems that apxs isn't installed by default and running a

apt-cache search apxs 

will throw up the packages needed to install it ... which in this case are

libapache-dev 

or something like that ...

---

### Post by kkass on 2006-09-08
Install apache2-threaded-dev

---

