---
title: "program ran by cron cannot talk to x server"
date: 2006-12-07
forum: General Help
---

### Post by harty83 on 2006-12-07
When I run a program via cron, I get an error that says that it cannot talk to the x server.  However if I run the program manually, it runs fine.  

How do I get around this problem?

Thanks!

---

### Post by dcstar on 2006-12-07
> **harty83 said:**
> When I run a program via cron, I get an error that says that it cannot talk to the x server.  However if I run the program manually, it runs fine.  

How do I get around this problem?

Thanks!

Various environment settings have to be defined for cron to work with X, do a forum search and you should find one of the many "HOWTO" posts on this issue.

---

### Post by harty83 on 2006-12-07
> **dcstar said:**
> Various environment settings have to be defined for cron to work with X, do a forum search and you should find one of the many "HOWTO" posts on this issue.

Ah thanks for the clue! I found a forum that said I needed to add "export DISPLAY=:0 && myscript" and it worked.  

Thanks!
Alan

---

