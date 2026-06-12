---
title: "package manager not working"
date: 2008-06-07
forum: General Help
---

### Post by JoaquimPosses on 2008-06-07
Error: opening the cache. (E:Type'<!DOCTYPE' is not know on line 1 in source list/etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.
It happened after I tried to install medibuntu to install acrobat reader (shame on me for using a edgy tutorial...).
Can anyone please help?

---

### Post by ibuclaw on 2008-06-07
Run these commands one by one:
```

sudo rm /etc/apt/sources.list.d/medibuntu.list

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
That should fix your problem

Regards
Iain

---

### Post by JoaquimPosses on 2008-06-21
It worked. Thank you.

---

### Post by grouchyolddude on 2008-06-24
> **tinivole said:**
> Run these commands one by one:
```

sudo rm /etc/apt/sources.list.d/medibuntu.list

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
That should fix your problem

Regards
Iain

rm: cannot remove `/etc/apt/sources.list.d/medibuntu.list': No such file or directory
 I recieve that error when attempting the first command that you've given.

---

