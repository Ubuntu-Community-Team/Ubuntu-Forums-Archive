---
title: "fetchmailconf stoped working"
date: 2007-03-20
forum: General Help
---

### Post by 65 mustang on 2007-03-20
Fetchmailconf was working just fine until i upgraded some packages.  Now i get the following error.  Any help is appreciated.

```
fetchmailconf
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/fetchmailconf.py", line 2064, in ?
    hostname = socket.gethostbyaddr(socket.gethostname())[0]
socket.gaierror: (-2, 'Name or service not known')
```

Thanks

---

