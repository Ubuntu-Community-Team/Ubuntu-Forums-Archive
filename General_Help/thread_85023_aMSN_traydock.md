---
title: "aMSN traydock"
date: 2005-11-01
forum: General Help
---

### Post by dJnEvS on 2005-11-01
i have got this error at amsn traydock configure
```
checking for Tk configuration... configure: WARNING: Can't find Tk configuration definitions

```
i have installed tcl/tk, but what sould i do?

---

### Post by RubenGonc on 2005-11-01
[QUOTE=dJnEvS]i have got this error at amsn traydock configure
```
checking for Tk configuration... configure: WARNING: Can't find Tk configuration definitions

```
i have installed tcl/tk, but what sould i do?[/QUOTE]

You have to install tcl-dev and tk-dev.

---

### Post by dJnEvS on 2005-11-01
i did...... :S
need some configuration or something i guess..

---

### Post by dJnEvS on 2005-11-01
help? some1

---

### Post by dJnEvS on 2005-11-01
[SOLVED] 
```
./configure --with-tk=/usr/lib/tk8.4/ --with-tcl=/usr/lib/tcl8.4/
```

---

### Post by Lord C on 2007-10-22
Nice one, thanks.

---

