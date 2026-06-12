---
title: "[SOLVED] changing apt-get repo?"
date: 2007-12-01
forum: General Help
---

### Post by TidusBlade on 2007-12-01
I an using Dapper Drake on a remote server through SSH terminal and I want to change the apt-get repo or wherever it saves things, to the gutsy one, any information regarding this would be appreciated :) Thanks in Advance!

---

### Post by -grubby on 2007-12-01
open a terminal and type:

```
gksudo gedit /etc/apt/sources.list
```

and change anything that says "dapper" to "gutsy" or just copy and paste the links one space below and then change "dapper" to "gutsy"

but I warn you, it may not work correctly because these apps may only work with gutsy

EDIT: or just copy and paste the following (one line below)

```
deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse

```

---

### Post by TidusBlade on 2007-12-01
Thanks alot! Quick response too :D

---

### Post by -grubby on 2007-12-01
> **TidusBlade said:**
> Thanks alot! Quick response too :D

glad to help

---

