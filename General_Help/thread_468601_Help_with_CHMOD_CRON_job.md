---
title: "Help with CHMOD CRON job"
date: 2007-06-09
forum: General Help
---

### Post by scott_ttocs46 on 2007-06-09
Hi all, 

     I need to change the permissions to a directory every minute. This is what I have in my cron tab:

```
* * * * * sudo /bin/chmod -R 777 * /www/localwww
```

      For some reason, it is not working. Any ideas?

Regards,
Scott

---

### Post by scott_ttocs46 on 2007-06-10
Seems like a relatively simple thing to do.

---

### Post by ipsi on 2007-06-10
Maybe this would help?

```
* * * * * **root** /bin/chmod -R 777 * /www/localwww
```

Not sure though. On the plus side, it won't break anything :)

---

