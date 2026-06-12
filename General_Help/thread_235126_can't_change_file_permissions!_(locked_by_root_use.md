---
title: "can't change file permissions! (locked by root user)"
date: 2006-08-12
forum: General Help
---

### Post by innocentegg on 2006-08-12
Ok i'm trying to edit a file that is locked by the root user.

I've tried logging in as root in the terminal then going back to see if i could edit the file, and this didn't work.

Any ideas?

---

### Post by aysiu on 2006-08-12
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) should help you.

---

### Post by Fass on 2006-08-12
```
man chmod
```

---

### Post by RRS on 2006-08-12
Try:
sudo nano /"file path"

Or maybe reboot into recovery mode. 

What file are you trying to edit? There may be something specific about it that someone could suggest a solution for.

edit; gotta' learn to type faster

---

### Post by aysiu on 2006-08-12
If you are going to do *sudo nano /path/filename*, I would highly advising popping a *-B* in there to back up the file: ```
sudo nano -B /path/filename
```

---

### Post by innocentegg on 2006-08-12
i've done it now guys (help via msn lol)

all i needed to do was type

```
sudo gedit sources.list
```

and type my password in. Thanks for replying anyway!

---

### Post by RRS on 2006-08-12
> **aysiu said:**
> If you are going to do *sudo nano /path/filename*, I would highly advising popping a *-B* in there to back up the file: ```
sudo nano -B /path/filename
```

Thanks for tip, I sometimes remmember to manually backup an important file before editing but didn't know about -B.

---

