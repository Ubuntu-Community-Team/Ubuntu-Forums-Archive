---
title: "impossible to remove server packages?"
date: 2007-06-12
forum: General Help
---

### Post by ericdfields on 2007-06-12
I did a minimal install of ubuntu... just the server stuff. I've been sshing into it just fine.

I started messing around with torrentflux and upon install, apt prompted me for some mysql information, which I supplied it, but it bombed somewhere along the process. In the mess that i've created (just a fun dev box... not mission critical), I can't seem to become a mysql root. 

I thought I'd just hose all the server packages, which I thought i did -- apt-get remove --purge apache2 php5 mysql-server -- but they all persist even though apt says they're not installed. I can type 'mysql' in the command line, and then tab, and see the full list of mysql commands. 

What could I be doing wrong?

Thanks

-- 
eric

---

### Post by kidders on 2007-06-14
Hi there,

> **ericdfields said:**
> apt-get remove --purge apache2 php5 mysql-serverIt doesn't look like anything is wrong ... mysql-server is a meta package, so removing it won't achieve much. If you want to uninstall your mysql server, try removing a "real" package. It'll probably be one of...```
dpkg --get-selections | grep mysql
```

---

