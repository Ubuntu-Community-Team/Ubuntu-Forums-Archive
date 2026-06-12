---
title: "make clean doesn't work"
date: 2007-10-16
forum: General Help
---

### Post by blurp on 2007-10-16
I have the following:
```

xxx@yyyr:~$ ls
makefile  x.a  x.b  x.c  x.d
xxx@yyy:~$ cat makefile 
.PHONY: all

all:
        -@rm x.{a,b,c,d}
xxx@yyy:~$ make
rm: cannot remove `x.{a,b,c,d}': No such file or directory
make: [all] Error 1 (ignored)

```

BUT, if I use
```

all:
        -@bash -c "rm x.{a,b,c,d}"

```
in the makefile, then those files get deleted!

Am I doing anything wrong here or is there a bug somewhere?

---

### Post by blurp on 2007-11-13
bump.

---

### Post by JasonF on 2007-11-13
The expansion of x.{a,b,c,d} is a feature bash, and presumably not implemented in make (It's not available in regular sh either)..

---

### Post by blurp on 2007-11-13
> **JasonF said:**
> The expansion of x.{a,b,c,d} is a feature bash, and presumably not implemented in make (It's not available in regular sh either)..

but this works if i issue the command it interactive gnome-terminal.. it is weird. after migrating from gentoo to ubuntu, all these makefiles don't work anymore... is there a better way of solving the problem than editing every single makefile?

---

### Post by JasonF on 2007-11-13
I figured it out, I don't know if it'll break anything later, but moving the link of /bin/sh to /bin/dash and remaking it to /bin/bash will allow the makefile to work.But is technically incorrect, the manual for gnu make says it only needs support for functionality avialable in normal 'sh'.

---

### Post by blurp on 2007-11-13
> **JasonF said:**
> I figured it out, I don't know if it'll break anything later, but moving the link of /bin/sh to /bin/dash and remaking it to /bin/bash will allow the makefile to work.But is technically incorrect, the manual for gnu make says it only needs support for functionality avialable in normal 'sh'.

i think dash is specific to ubuntu only. does this mean that dash has a bug? or does it mean that the x.{a,b,c} expansion cannot be assumed to be available in 'sh'?

---

### Post by blurp on 2007-11-22
answer is found in [https://wiki.ubuntu.com/DashAsBinSh]("https://wiki.ubuntu.com/DashAsBinSh")

but don't just mv sh to bash. use dpkg-reconfigure as suggested in the article.

---

