---
title: "Nautilus FTP Integration stopped working"
date: 2006-11-06
forum: General Help
---

### Post by glennric on 2006-11-06
I have always been able to connect to ftp sites using nautilus ftp integration.  However, today it stopped working.  If I enter the ftp address into the location and hit enter the password prompt comes up.  I enter the password for the site and hit enter and all that happens is another password prompt appears.  This will go on for all eternity if I keep pressing enter (I know because I tried it that long).  Was there an update of some sort that went awry or did something go wrong with my system in particular?  Does anyone know how to fix it?

---

### Post by taurus on 2006-11-06
See if you can connect to that ftp server from a terminal, Applications -> Accessories -> Terminal!  If you can, then there is something wrong with nautilus; otherwise, there could be something wrong with the server...

```
ftp ip_address
```

---

### Post by glennric on 2006-11-06
Yeah, I thought of that right after I posted and discovered that was the problem.  So ignore this thread.

---

### Post by fragos on 2006-11-06
I ran into something like this once.  The hosting provider made me login for each page I tried access.

---

### Post by Myrgen on 2006-12-14
I've had the same problem, and posted a solution in [this thread]("http://ubuntuforums.org/showthread.php?t=313515&highlight=nautilus+ftp")
Maybe it'll help?

---

### Post by Rodneyck on 2006-12-14
There is ftp support through nautlus?  How does that work?

---

### Post by mcduck on 2006-12-14
Press ctrl-L and type 'ftp://your.address.here'  to the location bar. Or go to Places/Connect to Server..

---

### Post by Rodneyck on 2006-12-14
> **mcduck said:**
> Press ctrl-L and type 'ftp://your.address.here'  to the location bar. Or go to Places/Connect to Server..

How did I miss that?  LOL... thanks a lot.

---

