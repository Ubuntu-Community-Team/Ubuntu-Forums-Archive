---
title: "libQtCore.so.4: cannot open shared object file: ---&gt; in ubuntu 20.04"
date: 2020-05-09
forum: General Help
---

### Post by habernir on 2020-05-09
hi all 

i have this error

error while loading shared libraries: libQtCore.so.4: cannot open shared object file: No such file or directory

i already install libqt5core5a but it want that pacakge
any idea how to solve this problem?

---

### Post by Yellow Pasque on 2020-05-09
Qt4 has been removed from Ubuntu 20.04
What are you trying to do/run that gives you the error?

---

### Post by ActionParsnip on 2020-05-09
What is the output of:
```

sudo updatedb
locate libQtCore.so.*

```

Thanks

---

### Post by habernir on 2020-05-09
Yellow Pasque - i'm installing redshift for houdini (its a renderer plugin for houdini)
and the license tool need "libQtCore.so.4" 

ActionParsnip - I get empty output.

but nevermind i searched and find this specific files and i put them in /lib/ and everythink ok

---

