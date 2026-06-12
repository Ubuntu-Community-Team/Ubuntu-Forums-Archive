---
title: "run sudo command from crontab"
date: 2007-07-10
forum: General Help
---

### Post by paincorp on 2007-07-10
im trying to restart my networking at /etc/init.d/networking in order to be able to reconnect to my wireless network which usually drops out atleast once a day.  i want to be able to run this via a crontab and a launcher on the desktop but cant figure out how to get it to work without having me enter a password (yes, i know its there for my own protection)

anyone know how this can be done?

---

### Post by mbeierl on 2007-07-10
The crontab one is easy.  Don't put it into your crontab, put it into root's!
```

sudo crontab -e

```
and then put your script in using cron's wonderful syntax.

As for the desktop shortcut, not sure...

Have you had any luck troubleshooting the wireless network?  Maybe we can help?

---

