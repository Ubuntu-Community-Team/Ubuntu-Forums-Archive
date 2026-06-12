---
title: "using command output as argument"
date: 2008-02-23
forum: General Help
---

### Post by Mr.Johnny on 2008-02-23
I'm trying to make a script that changes the nice of some programs according to their pid, I can currently isolate the pid with $ ps ax -l | grep myprogram | grep -c11-16 (something like this), but I don't know how how to use it as an argument to the renice command, i've tried several ways and none worked... :confused: how do I do this? 

thanks

---

### Post by lncoll on 2008-02-23
You can use

```
renice 7 -p `ps ax -l | grep progname | grep ...`
```

All the commands between `` are executed before renice and the output used as the parameter value.

---

### Post by Mr.Johnny on 2008-02-23
Dope! I didn't know there was a difference between ` and '.

Thanks, mate ;) that did it. kudos for you.

---

