---
title: "Why does apache still restart intself on Sundays?"
date: 2007-06-11
forum: General Help
---

### Post by alimovz on 2007-06-11
Hey guys. I have an SSL cert installed on my box and restarting it requires entering the passphrase. The log rotation restarts apache every Sunday morning and, of course, never brings it up. 
I use piped logging to avoid this situation. Here are the lines I have in the apache2.conf file:
```

ErrorLog "|/usr/sbin/rotatelogs /var/log/apache2/errorlog.%Y-%m-%d-%H_%M_%S 5M"
CustomLog "|/usr/sbin/rotatelogs /var/log/apache2/access_log 86400" common

```

But apache still restarts very Sunday even though the lines above work,  the logs do rotate according to them. I see it in the log directory. 

Why is it happening. Anybody?

Thanks

---

