---
title: "Pidgin Gthread Error"
date: 2007-10-09
forum: General Help
---

### Post by Zarathu on 2007-10-09
```
./configure && make && sudo make install
```

Of course.  After installing, I get this error:

```
zarathu@jesus:~$ pidgin

GThread-ERROR **: file gthread-posix.c: line 140 (): error 'Function not implemented' during 'pthread_getschedparam (pthread_self(), &policy, &sched)'
aborting...
Aborted (core dumped)
zarathu@jesus:~$ :(

```

Any ideas?  I googled the error but the suggestions that fixed others' problems didn't solve mine.

Thanks in advance.

Nick

---

### Post by alexsmith on 2007-11-27
I'm also having the same problem...

Alexandre Heitor Schmidt
[http://www.solis.coop.br/~alexsmith](http://www.solis.coop.br/~alexsmith)

---

### Post by penguin42 on 2007-12-23
I suspect you have the libpthread-dev and/or libpthread20 packages installed; remove them and it fixes similar problems when building rhythmbox for me.

See bug #178266

---

