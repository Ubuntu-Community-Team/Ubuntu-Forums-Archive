---
title: "Headless home backup server sending thousands of requests to a mail domain."
date: 2017-01-27
forum: General Help
---

### Post by PartisanEntity on 2017-01-27
Hi there,

I have a headless Ubuntu home backup server. I have recently noticed that it is sending out about 4300 requests per minute to mail.example.home

example.home is the hostname I have configured in /etc/hosts:

```
127.0.0.1       localhost
127.0.1.1       server.example.home    server
```


How could I isolate this issue and prevent it from happening? What can I check?

---

### Post by PartisanEntity on 2017-01-27
OK after some digging around it turned out to be raid monitoring of mdadm through webmin. I disabled it and it stopped.

---

### Post by Habitual on 2017-01-27
Good job and well done, sir!
I was sorta looking in or around /etc/aliases :)

---

