---
title: "Need to access upgrade log : how to ?"
date: 2006-11-11
forum: General Help
---

### Post by Browser_ice on 2006-11-11
How do I access the upgrade log ?

I saw a bunch of errors and warnings in the upgrade process while going from 6.06 to 6.10

I haven't rebooted yet. Don't want to find myself with a dead system.

I can't tell you what I saw cause the scrolling was too fast and I couldn't copy paste.

---

### Post by moshuptrail on 2008-01-11
no one has been able to answer this so I'll try
when doing an upgrade from a CD I found log info in /var/log/syslog
I don't know if doing an upgrade from the Update Manager uses the same log

---

### Post by chrisccoulson on 2008-01-11
I'm not sure if it will contain any useful information, but dpkg writes to /var/log/dpkg.log

---

