---
title: "Disabling MySQL and Apache"
date: 2007-09-08
forum: General Help
---

### Post by honda882000 on 2007-09-08
I have recently installed MySQL, Apache and even Oracle Express in order to play around and learn a few things about web servers, but now my computer is running extremely slow (specially due to Oracle) since all these servers are on at startup.  I manually disable each one every time I startup, but I was wandering if anyone could tell me how to configure Apache and MySQL so that they only turn on manually, and not at startup.  Thanks!

---

### Post by jamvegan on 2007-09-08
The easiest way is to go to System->Administration->Services and uncheck them.  If any of them do not appear in the menu (and they will probably be listed by type of server--something like Database Server (mysql)), reply here and we'll go into command line methods of preventing them from starting at boot.

---

