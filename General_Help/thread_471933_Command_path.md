---
title: "Command path"
date: 2007-06-12
forum: General Help
---

### Post by iAlta on 2007-06-12
What's it called and where is the file located, the one that lists all the commands and the locations of the binaries?

---

### Post by dreadlord_chris on 2007-06-12
> **iAlta said:**
> What's it called and where is the file located, the one that lists all the commands and the locations of the binaries?

HUH?
Are you talking about *whereis*:
```

chris@HAL421:~$ whereis whereis
whereis: /usr/bin/whereis /usr/X11R6/bin/whereis /usr/bin/X11/whereis /usr/share/man/man1/whereis.1.gz

```

or perhaps you mean *which*:
```

chris@HAL421:~$ which whereis
/usr/bin/whereis

```

you could also try *help*:
```

chris@HAL421:~$ help
GNU bash, version 3.2.13(1)-release (i486-pc-linux-gnu)
These shell commands are defined internally.  Type `help' to see this list.
Type `help name' to find out more about the function `name'.
Use `info bash' to find out more about the shell in general.
Use `man -k' or `info' to find out more about commands not in this list.

A star (*) next to a name means that the command is disabled.

 JOB_SPEC [&]                       (( expression ))
 . filename [arguments]             :
 [ arg... ]                         [[ expression ]]
 alias [-p] [name[=value] ... ]     bg [job_spec ...]
...

```

Then again, there is also *man*:
```

chris@HAL421:~$ man man
Reformatting man(1), please wait...

MAN(1)               Manual pager utils                  MAN(1)

NAME       man - an interface to the on-line reference manuals

SYNOPSIS
....

```

---

### Post by tszanon on 2007-06-12
Are you talking about *whereis*? Something like:
```
> whereis firefox
/usr/sbin/firefox
```
I think that whereis can tell you where it is if you type **whereis whereis** :)

---

### Post by iAlta on 2007-06-12
no it's not whereis

it's like, how does the system know where whereis is?

---

### Post by taurus on 2007-06-12
It's the $PATH.

```
echo $PATH
```

---

### Post by iAlta on 2007-06-13
Thanks you! That was it...

---

