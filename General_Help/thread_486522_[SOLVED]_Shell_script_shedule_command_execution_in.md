---
title: "[SOLVED] Shell script: shedule command execution in 10 s"
date: 2007-06-28
forum: General Help
---

### Post by Elegorod on 2007-06-28
I've added a command
```
sudo pon inet
```
to my /etc/rc.local to turn on internet connection on system start.
How to make this command executed not immediately, but in 10 second after rc.local script execution.
```
sleep 10s
``` is NOT right, because it blocks script execution.

---

### Post by nichipet on 2007-08-01
Are you still looking for a solution to this? If so, I can take a look at it and try to find an answer.

---

### Post by Elegorod on 2007-08-09
Yes, I still don't know how to do it. Try to look, please.
Is it possible without writing a program on C or similar programming language?

---

### Post by muddymind on 2007-08-09
> **Elegorod said:**
> I've added a command
```
sudo pon inet
```
to my /etc/rc.local to turn on internet connection on system start.
How to make this command executed not immediately, but in 10 second after rc.local script execution.
```
sleep 10s
``` is NOT right, because it blocks script execution.

You could put it in a separate script file like this

```
#!/bin/bash
sleep 10s
pon inet
```

and in rc.local you could put something like this:

```

/path_to_script/script **&**
```

That way It wont stop at sleep but runs it in parallel..

[]

ps-I don't think you need to put sudo's in rc.local...

---

### Post by Elegorod on 2007-08-10
Thanks! It really works.
Sudo is not needed, and I've set my script executable (chmod +x /path_to_script/script)

---

