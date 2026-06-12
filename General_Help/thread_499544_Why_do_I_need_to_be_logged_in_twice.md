---
title: "Why do I need to be logged in twice?"
date: 2007-07-12
forum: General Help
---

### Post by B-Con on 2007-07-12
If I run the "users" command I see myself logged in twice:
```
b-con@beacon:~$ users
b-con b-con

```

If I run the "who" command I see myself logged in twice:
```
b-con    :0           2007-07-12 14:27
b-con    pts/0        2007-07-12 14:31 (:0.0)

```

The "tty" command shows that I'm using /dev/pts/0 (like the "who" command just showed).

I'm somewhat confused about what the pts/*'s are, and why I need to be "logged in" twice for it. What's the first login and why do I need a seperate login for the /dev/pts/0 ?

---

### Post by Cappy on 2007-07-12
One login is you running gnome, the second is you using the terminal.

---

### Post by B-Con on 2007-07-13
Why do I need to be logged in twice for that, though? I don't have to login again for every other application I run.

---

### Post by Mr. C. on 2007-07-13
Your concept of "logged in" is more Windows-centric, and doesn't really apply directly to a multi-user, Linux/Unix environment where it is routine for multiple shells to be running on a users behalf.  What you see is two shells processes running with your UID/GID, which happen to have been specified as "login shells".  This has specially meaning, such as which startup files to process, whether or not the shells show up in commands such as **last**, **who**, **users**, etc.

Also see my response here:

See my reply here:
[http://ubuntuforums.org/showthread.php?t=493650&highlight=mrc+login+shell](http://ubuntuforums.org/showthread.php?t=493650&highlight=mrc+login+shell)

In Windows, there are often multiple processes running on your behalf as well; you just don't see them without looking for them.

MrC

---

### Post by B-Con on 2007-07-15
Ah, thanks. Turned out I needed to understand login shells better.

Cheers. :)

---

