---
title: "permissions"
date: 2006-07-05
forum: General Help
---

### Post by lex1 on 2006-07-05
Here is a line in /etc/suck

-rw-r--r--  1 news root  122 2006-07-05 11:15 sucknewsrc

how do i change the permissions so it reads:

-rw-r--r--  1 news news  122 2006-07-05 11:15 sucknewsrc?

lex1

---

### Post by Ramses de Norre on 2006-07-05
```
sudo chown lex1 /etc/suck/news && chmod 644 /etc/suck/news
```

---

