---
title: "I need a key for freecontribs repo"
date: 2006-11-08
forum: General Help
---

### Post by TheRingmaster on 2006-11-08
I need a key for this respository: 
# Penguin Liberation Front (packages)
 deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) edgy-plf free non-free

---

### Post by o_fortuna on 2006-11-08
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```
Should do the trick

---

### Post by TheRingmaster on 2006-11-09
thanks

---

