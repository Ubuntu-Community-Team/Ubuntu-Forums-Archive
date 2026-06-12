---
title: "Not man for set?"
date: 2015-07-13
forum: General Help
---

### Post by cowboy.bebop on 2015-07-13
Why is there no manual entry for 'set'?

I try 
```
:~$ man set
```

with 0 results, but then get 
```
:~$ set --help
set: usage: set [-abefhkmnptuvxBCHP] [-o option-name] [--] [arg...]
```

With no explanation at all. How do I know what all the arguments do?

---

### Post by coldraven on 2015-07-13
I don't know why there is no man information but a quick search found these:
[http://www.computerhope.com/unix/uset.htm](http://www.computerhope.com/unix/uset.htm)
[http://linux.about.com/library/cmd/blcmdln_set.htm](http://linux.about.com/library/cmd/blcmdln_set.htm)

---

### Post by cowboy.bebop on 2015-07-13
Nice, ty. Is it common for ubuntu not to have a manual entry for set?

---

### Post by steeldriver on 2015-07-13
It's a shell builtin rather than a standalone command - either use

```

help set

```

or look in the bash manpage under the section SHELL BUILTIN COMMANDS

---

### Post by grahammechanical on 2015-07-13
Manpages come with Linux. 

[https://help.ubuntu.com/community/man](https://help.ubuntu.com/community/man)

Regards.

---

