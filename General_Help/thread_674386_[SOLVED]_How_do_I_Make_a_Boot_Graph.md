---
title: "[SOLVED] How do I Make a Boot Graph?"
date: 2008-01-21
forum: General Help
---

### Post by Het Irv on 2008-01-21
I have seen people post a graph of what processes are running and how long they run as a diagnostic tool.  I am not having any problems right now I just would like to know how to look at mine.

Thanks in Advance.

---

### Post by danwood76 on 2008-01-21
do a
```
 sudo apt-get install bootchart
```

it will then automatically create boot graphs in:
/var/log/bootchart/

regards,
Danny

---

