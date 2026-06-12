---
title: "Removed python, messed up ubuntu-desktop - how to have two python versions running?"
date: 2007-12-05
forum: General Help
---

### Post by FFighter on 2007-12-05
Hello,

I'm starting to work with the Zope application server. I have downloaded it and tried to start the ZServer but it told me it required Python 2.4.4. Gutsy comes preloaded with Python 2.5.1. I thought no part of the system was dependent on python but when I tried to remove it using aptitude, my ubuntu-desktop (Gnome) was also uninstalled. 

Luckily I was able to get it running again by re-installing the ubuntu-desktop package using aptitude.

How could I get two python versions on the same system? 

Thanks,

Marcelo.

---

### Post by metalheart on 2007-12-05
If the required version is older, then it should work with newer too.

---

### Post by pointone on 2007-12-05
```
sudo apt-get install python2.4
```

---

