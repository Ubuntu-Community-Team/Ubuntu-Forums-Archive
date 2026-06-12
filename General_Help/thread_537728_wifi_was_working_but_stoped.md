---
title: "wifi was working but stoped"
date: 2007-08-29
forum: General Help
---

### Post by zach12 on 2007-08-29
hi  
a few days ago i started up one of my laptops (it's a dell inspieon 7500 runs 7.04 ubuntu).  And the wifi was not working. I had set it to roaming mode it had been working for weeks
and now it's not working. i did > cat /etc/network/interfaces
 and everything looks ok so. I don't know what is the problem is
thanks

---

### Post by tgalati4 on 2007-08-29
I also have a Dell Inspiron 7500, but I am running Dapper.  I am also having wireless problems.  It was working fine, then (after a series of updates perhaps) I can't seem to connect.  I go into wifi radar and physically hit connect button and it sometimes reconnects.

I looks like a timing issue, some process is interferring with the DHCP assignment, or with the wireless tuning and it fails.  Perhaps I need to put a sleep command somewhere.

---

### Post by zach12 on 2007-08-29
hmm ok thanks

---

