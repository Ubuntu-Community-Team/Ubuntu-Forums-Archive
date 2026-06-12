---
title: "dpkg --configure need superuser privilege!"
date: 2005-10-28
forum: General Help
---

### Post by serlex on 2005-10-28
ok just tried to install build-essentials. but i get error message

```
 dpkg was interrupted
```
so i type
```
dpkg --configure -a
```
then it says
```
requested operation requires superuser privilege
```

:(

---

### Post by Ali_Baba on 2005-10-28
Hi,put a word sudo before,like sudo dpkg --configure -a.Then it asks your password and after that it should work :)

---

### Post by serlex on 2005-10-28
lol, thanks, but cant install sudo apt-get install build essential
```
 Could not get lock /var/lib/dpkg/lock - open (11 resource temporarily unavailable)
Unable to lock the administration directory (var/lib/dpkg/), is another process using it?

```
?

---

### Post by soonindallas on 2005-10-28
do you happen to have synaptic open ?

---

### Post by serlex on 2005-10-28
:s might aswell admit, yes i did, oh well, thats why im doing computer tech :P.

---

### Post by soonindallas on 2005-10-28
you're welcome

I recognised it 'cos it's not the first time I've seen that error.... I get it often in my own terminal ;)

---

