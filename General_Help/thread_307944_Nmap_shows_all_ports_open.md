---
title: "Nmap shows all ports open"
date: 2006-11-27
forum: General Help
---

### Post by shokora on 2006-11-27
I'm sorry if this question is asked before, i used the search function and didn't find anything usefull.

I have a huge problem with nmap that i never had with another distro. When i try to nmap some host, it says all ports are open (while they obviously aren't). I mainly use this syntax:
```
 nmap -sS -sV -vv -O host 
```

When other people try the exact same thing on the same host, they do get a normal result. Can anyone please tell me why i get this, and how to fix it?

(scanning internal ip adresses does work normally).

stats:
ubuntu 6.10
i686
kernel 2.6.17-10
KDE 3.5.5 / 3.3.6

btw, first i thought the package on the apt servers was borked so i compiled my own nmap 4.11 and i have the same problem.

---

### Post by bswilson on 2006-11-27
I think you need to use **sudo** to invoke proper **nmap** results.  Also, using -sS and -sV could be causing a problem.  I think you're supposed to use one or the other...

---

### Post by ~LoKe on 2006-11-27
Must be an nmap problem.  I get the same results without using **-sS -sV -vv -O**.

**EDIT:** It's possible that they're showing open ports that aren't really there, intentionally.

---

### Post by shokora on 2006-11-27
ofcourse i do this while being root ;)

yes, it is possible that they do this intentionally, but as i said before. If i ask other people to scan the same host, they do get a normal result while i get all the ports open o.o

---

### Post by ~LoKe on 2006-11-27
Which host are you trying to scan?

---

### Post by fragos on 2006-11-27
You can scan any host with nmap, yourself, a router you're connected to or anyone else on the Internet.

---

### Post by shokora on 2006-11-28
> **~LoKe said:**
> Which host are you trying to scan?

every host i try to scan i get the same thing, while if i try it with [http://nmap-online.com/](http://nmap-online.com/) i do get normal results o.o

---

