---
title: "killproc: command not found"
date: 2007-03-03
forum: General Help
---

### Post by Valiante on 2007-03-03
My lighttpd stop|start|restart script uses the killproc command but it wasn't working.

When I tried the killproc command manually in the console it returned the following error;

```
 killproc: command not found
```

Is there an alternative in Ubuntu?

---

### Post by RedSquirrel on 2007-03-03
There's a killproc in /lib/lsb/init-functions.

---

### Post by annda on 2007-03-03
ckeck out kill and killall

---

### Post by Valiante on 2007-03-03
Cheers guys...  in the meantime a friend of mine (a linux veteran) scp'd a functions script to me which, once copied to init.d, allowed me to use killproc.

Thanks for the replies though!

---

### Post by howser on 2007-07-25
> **Valiante said:**
> Cheers guys...  in the meantime a friend of mine (a linux veteran) scp'd a functions script to me which, once copied to init.d, allowed me to use killproc.

Thanks for the replies though!

Any chance one of you post the file?  Or if it's too large direct me to somewhere I can download it.

---

