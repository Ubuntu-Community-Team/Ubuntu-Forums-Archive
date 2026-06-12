---
title: "Crontab Alarm Clock"
date: 2013-03-28
forum: General Help
---

### Post by hhaydoura on 2013-03-28
Hello, I want to make a Crontab schedule for an alarm, to ring on these specific minutes.. every day on Monday till Friday.. at 8.55, 9.00, 9.55, 10.00, 10.55, 11.00, 11.55, 12.00, and 12.30 and 13.30...
How is that possible and plz tell me the steps to do that;
Many thanks :)

---

### Post by 2013james on 2013-03-29
Try the interactive cron simulator CronSandbox at [http://www.dataphyx.com](http://www.dataphyx.com). It will let you try out any combination of crontab timing commands and show you a list of future run-times.

---

### Post by btindie on 2013-03-29
> **hhaydoura said:**
> every day on Monday till Friday.. at 8.55, 9.00, 9.55, 10.00, 10.55, 11.00, 11.55, 12.00, and 12.30 and 13.30...

You'd have to split it into multiple schedules based on the times given.
```
55 8-11 * * 1-5 COMMAND
00 9-12 * * 1-5 COMMAND
30 12-13 * * 1-5 COMMAND
```

---

