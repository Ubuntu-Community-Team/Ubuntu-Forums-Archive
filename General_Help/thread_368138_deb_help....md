---
title: "deb help..."
date: 2007-02-22
forum: General Help
---

### Post by hippieh8er15 on 2007-02-22
Im trying to install beryl and xgl and the process says to type 

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy (latest: beryl 0.1.1)

but when i enter it in the terminal it says 

command not found what do i need to do to make this work?

---

### Post by zanglang on 2007-02-22
You need to enter the line into the /etc/apt/sources.list file for apt to use, not in straight in console. 'sudo gedit /etc/apt/sources.list' first, then paste the line 'deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy' in there. ;)

---

### Post by hippieh8er15 on 2007-02-22
> **zanglang said:**
> You need to enter the line into the /etc/apt/sources.list file for apt to use, not in straight in console. 'sudo gedit /etc/apt/sources.list' first, then paste the line 'deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy' in there. ;)

Thank you

---

