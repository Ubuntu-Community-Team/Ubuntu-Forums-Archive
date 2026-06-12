---
title: "multiples services (daemons) running for the same pourpose"
date: 2005-10-19
forum: General Help
---

### Post by faustobp on 2005-10-19
Running services-admin it shows 3 types of cron (anacron, atd and cron) and 2 sys loggers (klogd and sysklogd) running (with checkbox checked). Is it right? Should I disable some of them (leaving just one cron an one syslogger)?

---

### Post by amohanty on 2005-10-19
I think you can disable atd and anacron without any major problems.

HTH
AM

---

### Post by temcat on 2005-10-20
[QUOTE=amohanty]I think you can disable atd and anacron without any major problems.

HTH
AM[/QUOTE]

I don't know about atd, but IIRC anacron runs slocate periodically. If you want to use locate command, you shouldn't disable anacron.

---

