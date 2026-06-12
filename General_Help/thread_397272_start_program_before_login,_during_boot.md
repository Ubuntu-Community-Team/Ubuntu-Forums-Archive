---
title: "start program before login, during boot?"
date: 2007-03-30
forum: General Help
---

### Post by twildt on 2007-03-30
How can I get a program to startup before login, I need this program to start automatically in case the server gets rebooted and is unknown!  

I tried the inittab file but it doesn't exist!!

Running Ubuntu 6.10

---

### Post by yabbadabbadont on 2007-03-30
Call the program from /etc/rc.local

rc.local is the last script that is run during boot up.

---

### Post by Happpiness on 2008-01-01
> **yabbadabbadont said:**
> Call the program from /etc/rc.local

rc.local is the last script that is run during boot up.

Thanks!

---

