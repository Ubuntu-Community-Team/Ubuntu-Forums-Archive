---
title: "Running Qt5 applications under ubuntu 12.10"
date: 2013-06-03
forum: General Help
---

### Post by mbnoimi on 2013-06-03
Whenever I tried to run any Qt 5 based application I got this error message:
```
error while loading shared libraries: libQt5Widgets.so.5: cannot open shared object file: No such file or directory
```

How can I run Qt5 based applications?

PS
I already have installed Qt5 SDK from Digia website under /opt/Qt_5.0.2 but nothing changed!

---

### Post by mbnoimi on 2013-06-04
HuntsMan & thiago answered me at #Qt irc channel:

[list=1]
[*]Add a new line to /etc/ld.so.conf: /opt/Qt_5.0.2/5.0.2/gcc_64/lib
[*]sudo ldconfig
[/list]

---

