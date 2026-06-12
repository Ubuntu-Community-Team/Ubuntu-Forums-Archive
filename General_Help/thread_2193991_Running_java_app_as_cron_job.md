---
title: "Running java app as cron job"
date: 2013-12-15
forum: General Help
---

### Post by wetsprocket on 2013-12-15
I'm trying to have a .jar file executed as a cron job at startup but nothing seems to be happening, I'm using crontab -e. Any ideas?

```
@reboot java -jar /home/user/app.jar >>&! /tmp/test.log
```

---

### Post by ian-weisser on 2013-12-15
What system resources or environment variables does the application expect? Displays to print to? Stdin to scan from? Current working directories? User accounts? Network? Paths to other commands?

---

