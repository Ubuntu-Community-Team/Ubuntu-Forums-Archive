---
title: "Problems with esudo and gksudo in ubuntu 14.04"
date: 2014-07-25
forum: General Help
---

### Post by %cV4BU£r8Ofp&amp;# on 2014-07-25
This is what happens when i put that commands in terminal. Same happens when i try to open any app using them (like "gksu synaptic").
```
:~$ esudo
Traceback (most recent call last):
  File "/usr/bin/esudo", line 5, in <module>
    import esudo.esudo as esudo
  File "/usr/lib/python2.7/dist-packages/esudo/esudo.py", line 13, in <module>
    import ecore
ImportError: No module named ecore

:~$ gksu
Traceback (most recent call last):
  File "/usr/bin/gksu", line 5, in <module>
    import esudo.esudo as esudo
  File "/usr/lib/python2.7/dist-packages/esudo/esudo.py", line 13, in <module>
    import ecore
ImportError: No module named ecore

```

Anybody knows how to make this work? Im not sure but i think this error is also causing that i can't open synaptic and some other apps which require root from the bar icon.

---

### Post by bapoumba on 2014-07-25
gksu is not installed by default anymore. If you are to run graphical applications as root, please use sudo -H or pkexec.
[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) < this page has not been updated yet.

---

### Post by grahammechanical on 2014-07-25
why do you expect an Enlightenment replacement for gksudo to be in Ubuntu?

[http://sourceforge.net/p/enlightenment/mailman/enlightenment-users/thread/CAKs0SrBkwCAYhcaENYgwX%2B3q2BA%2BNnENchSTe3EPddyZpnWftQ@mail.gmail.com/](http://sourceforge.net/p/enlightenment/mailman/enlightenment-users/thread/CAKs0SrBkwCAYhcaENYgwX%2B3q2BA%2BNnENchSTe3EPddyZpnWftQ@mail.gmail.com/)

gksu is still in the Ubuntu repositories but the Ubuntu developers view it as depreciated. Which means its days are numbered. Are you running Enlightenment? Or a distribution based upon Ubuntu that uses Enlightenment? You should make stuff like that clear in your post.

Regards.

---

### Post by %cV4BU£r8Ofp&amp;# on 2014-07-25
i've used enlightenment desktop but i've unistalled it, maybe i did a wrong unistall.

---

