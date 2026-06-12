---
title: "WINE directory??"
date: 2005-09-08
forum: General Help
---

### Post by X5-655 on 2005-09-08
In installed a Windows application in WINE to C:\Program Files, but where in the world do I get to that??

I really need to execute the application that went into Program Files, and no obvious pointers can be found..

---

### Post by drummer on 2005-09-08
[QUOTE=X5-655]In installed a Windows application in WINE to C:\Program Files, but where in the world do I get to that??

I really need to execute the application that went into Program Files, and no obvious pointers can be found..[/QUOTE]
 From memory, it's a hidden folder in your home directory called .wine/
in that there is 'fake_c' or something similar which contains what you'd find on the c drive in a windows install.

---

### Post by X5-655 on 2005-09-08
[QUOTE=drummer]From memory, it's a hidden folder in your home directory called .wine/
in that there is 'fake_c' or something similar which contains what you'd find on the c drive in a windows install.[/QUOTE]
thanks..  though, Wine fails to load the application I needed to run..  It installed it, but won't run it..

it's for my A+ certification, and as soon as I enter my username and password, it freezes...   ](*,)

---

### Post by drummer on 2005-09-12
are you running it with```
wine installedprogram.exe
```??

---

