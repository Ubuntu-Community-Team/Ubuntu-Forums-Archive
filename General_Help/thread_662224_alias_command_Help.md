---
title: "alias command Help"
date: 2008-01-08
forum: General Help
---

### Post by ryankask on 2008-01-08
I have this in my .bashrc

alias ls='ls -l --color=auto --ignore=+(#*#|*~*~|*.tmp)'

Is something wrong with my pattern?

Thanks,
Ryan Kaskel

---

### Post by dagnabit dang doohickey on 2008-01-08
Use the ignore option multiple times; ignore each pattern separately:
```
alias ls='ls -l --color=auto --ignore=#*# --ignore=*~*~ --ignore=*.tmp'
```
or the short form:
```
alias ls='ls -l --color=auto -I #*# -I *~*~ -I *.tmp'
```

---

### Post by ryankask on 2008-01-09
you are the man, appreciate it!

---

### Post by ryankask on 2008-01-09
By the way, good alias if you do Python development in emacs:

```

alias ls='ls -l --color=auto --ignore=#*# --ignore=*~*~ --ignore=*.tmp --ignore *.pyc'

```

...by the way the short -I form gives me errors:
```

alias ls='ls -l --color=auto -I #*# -I *~*~ -I *.tmp -I *.pyc'

```
ryan@rlk-linux:~$ ls
ls: option requires an argument -- I
Try `ls --help' for more information.

---

### Post by dagnabit dang doohickey on 2008-01-09
Its choking on the pound character. Escaping the # or quoting the pattern seems to solve it.
```
alias ls='ls -l --color=auto -I \#*\# -I *~*~ -I *.tmp'
```
```
alias ls='ls -l --color=auto -I "#*#" -I "*~*~" -I "*.tmp"'
```
*I quoted all patterns in the second example just for uniformity.

---

