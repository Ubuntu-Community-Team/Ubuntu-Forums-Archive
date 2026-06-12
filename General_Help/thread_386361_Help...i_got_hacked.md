---
title: "Help...i got hacked ?"
date: 2007-03-16
forum: General Help
---

### Post by gtcoffee on 2007-03-16
how come there is 2 users and 1 zombie ??
is that mean i got hacked ?? if so what should i do......help....!!

```
top - 23:04:13 up 1 min,  2 users,  load average: 1.00, 0.46, 0.17
Tasks: 130 total,   1 running, 128 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.3%us,  1.0%sy,  0.0%ni, 95.5%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1034600k total,   333196k used,   701404k free,     8476k buffers
Swap:   530136k total,        0k used,   530136k free,   192328k cached
```

---

### Post by gtcoffee on 2007-03-16
how come there is 2 users and 1 zombie ??
is that mean i got hacked ?? if so what should i do......help....!!

```
top - 23:04:13 up 1 min,  2 users,  load average: 1.00, 0.46, 0.17
Tasks: 130 total,   1 running, 128 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.3%us,  1.0%sy,  0.0%ni, 95.5%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1034600k total,   333196k used,   701404k free,     8476k buffers
Swap:   530136k total,        0k used,   530136k free,   192328k cached
```

---

### Post by kevinlyfellow on 2007-03-16
thats normal, [http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)

to see whos logged into your computer, type
```
who
```

---

### Post by taurus on 2007-03-16
When you log into Gnome, that's one user.  And if you open a terminal, that would be two users.

What's the output of this command from a terminal?

```
finger
```

---

### Post by gtcoffee on 2007-03-16
oh, thanks taurus...
you are right, its one for Gnome, one for terminal...
and i opened two terminal and it shows up 3 users...

btw, i got pissed off, and restart my pc immediately -_- !!

---

### Post by scxtt on 2007-03-16
if you want to know which process is a zombie, do **ps -ef | grep defunct** ...

---

### Post by gtcoffee on 2007-03-16
oh someone told me y there r 2 users,
becoz its 1 for gnome and 1 for terminal..

kevinlyfellow thanks for helping =]

---

### Post by scxtt on 2007-03-16
a "zombie" doesn't have anything to do w/ that ... in the future, if you see a zombie and want to know what process is zombified - run the command i gave above ...

---

### Post by maxamillion on 2007-03-16
every terminal window you have open is a "user" ... i don't think you got hacked, 1 user is the :0 which is your X (Desktop) login, and another user is the terminal window you have opened to run top which is seen as pts/0

---

