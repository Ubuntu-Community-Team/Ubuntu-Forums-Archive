---
title: "ubuntu 16.04 how to get independent, but concurrent remote connections"
date: 2016-10-17
forum: General Help
---

### Post by mauxm on 2016-10-17
hi,
does someone know how to get independent, but concurrent remote connections with ubuntu 16.04. 
it is possible to get several x11vnc remote connections at the same time, but they are not independent to work with.
every new connections shares the same screen, that nobody can work independently.
thanks in advance for helping me 
cheers

---

### Post by TheFu on 2016-10-17
> **mauxm said:**
> hi,
does someone know how to get independent, but concurrent remote connections with ubuntu 16.04. 
cheers

Use ssh.

If you need different remote GUI sessions, use different userids. There might be an option to force multiple sessions - I'd have to check the manpage, which you can do just as easily.  

Or use x2go.

---

