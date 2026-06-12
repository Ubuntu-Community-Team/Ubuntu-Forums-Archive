---
title: "SPE installation"
date: 2005-09-30
forum: General Help
---

### Post by var on 2005-09-30
hi all,
I'm trying to install the SPE Python editor, version 0.7.5.c, under Ubuntu Hoary.
it needs the version 2.6.1.0 of wxPython, so I added these repositories:
```

deb http://www.vollstreckernet.de/debian/ testing amule
deb http://www.vollstreckernet.de/debian/ testing wx
deb-src http://www.vollstreckernet.de/debian/ testing amule
```
but, when I try to install the new version of wxPython, I obtain this result:
```
wxpython2.6-0:
Depends: libwxgtk2.6-0-python will not be installed
```
and I can't proceed.
how can I fix this situation?
thanks a lot. :)

---

### Post by Zotova on 2005-09-30
It seems that the program depends on libwxgtk2.6-0-python - so you need to install libwxgtk2.6-0-python first and then install the program you are trying to install.

---

### Post by var on 2005-09-30
[QUOTE=Zotova]It seems that the program depends on libwxgtk2.6-0-python - so you need to install libwxgtk2.6-0-python first and then install the program you are trying to install.[/QUOTE]
first of all, thank you for your answer. :)
when I try to install libwxgtk2.6-0-python I obtain this result:

[http://var.altervista.org/img/problems.png](http://var.altervista.org/img/problems.png) (copy this address in your address bar and reload)

as you can see, it seems that I have problems with dependences. :|

---

### Post by var on 2005-09-30
up

---

### Post by UbuWu on 2005-10-01
Luckily it is in the breezy repositories :D So if you wait two weeks and upgrade, you will save yourself a lot of trouble.

---

### Post by var on 2005-10-01
[QUOTE=UbuWu]Luckily it is in the breezy repositories :D So if you wait two weeks and upgrade, you will save yourself a lot of trouble.[/QUOTE]

yep, I know this (and also that it's the only solution): so, I'll wait a while. :)
thanks a lot. ;)

---

### Post by stani on 2006-07-18
Read my [howto install latest wxPython & SPE (Feature rich Python IDE)]("http://www.ubuntuforums.org/showthread.php?t=218001&highlight=wxpython").

---

