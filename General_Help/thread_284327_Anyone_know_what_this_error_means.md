---
title: "Anyone know what this error means"
date: 2006-10-25
forum: General Help
---

### Post by BlocknBleed on 2006-10-25
Trying to install a game and during the ./configure it shows a line with this.

configure: WARNING: Enable Debuging

anyone know how to enable debuging.

---

### Post by po0f on 2006-10-25
BlocknBleed,

```
$ ./configure --help
```
?

---

### Post by tronica on 2006-10-25
you might try

> ./configure --enable-debug

---

### Post by BlocknBleed on 2006-10-25
> **tronica said:**
> you might try

Tryed that and different variations of it. still have the WARNING:

---

### Post by tronica on 2006-10-25
ok, well.....lets see

> ./configure --enable-quietcompile --disable-debug

or

> ./configure --enable-quietcompile --enable-debug

try that one.

---

### Post by BlocknBleed on 2006-10-25
./configure --enable-quietcompile --disable-debug

seemed to work. thanks.

btw what does quietcompile do?

---

### Post by tronica on 2006-10-25
If this option it used it won't output errors.

---

