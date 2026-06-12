---
title: "Running Cron (solved)"
date: 2006-11-01
forum: General Help
---

### Post by PriceChild on 2006-11-01
Ok... so...```
$ crontab -l
# m h  dom mon dow   command
0 5/* * * * /usr/local/bin/wallpaper
```Which i hope means every 5 minutes it will run the script... but it doesn't.

The script runs fine from terminal.

Please help :)

Pricey

---

### Post by krismatth3 on 2006-11-01
If I'm reading your output correctly, you've set it to run every 5 hours, instead of every five minutes. Can you try the config below?
> 
*/5 * * * * /usr/local/bin/wallpaper


---

### Post by ianmacgregor on 2006-11-01
> **PriceChild said:**
> Ok... so...```
$ crontab -l
# m h  dom mon dow   command
0 5/* * * * /usr/local/bin/wallpaper
```Which i hope means every 5 minutes it will run the script... but it doesn't.

The script runs fine from terminal.

Please help :)

Pricey

This might be of interest:
[http://ianmacgregor.org/wiki/Linux/CrontabTutorial](http://ianmacgregor.org/wiki/Linux/CrontabTutorial)

---

### Post by PriceChild on 2006-11-01
Thanks guys :D

now 5 mins to see if it works :)

EDIT Perfect :D

---

