---
title: "cron entry runs multiple times"
date: 2018-08-15
forum: General Help
---

### Post by markaurit on 2018-08-15
I have a script I want to run 1 time each day, at 1am. The script performs a brief and simple postgres update, which returns a datestamp and the # of updates, 
and appends them to a file.

 The crontab entry is: * 01 * * * <script>

It runs; however it fires every minute for that hour. Conceptually I can think of how the asterisk in the first parameter (minute) is causing that, but all the examples
I see on web pages seem to ignore this as happening

postgres output looks like:
2018-08-21, 01:00:00, 8192
2018-08-21, 01:01:00, 8192
2018-08-21, 01:02:02, 8192
..
..
..
2018-08-21, 01:59:00, 8192

---

### Post by SeijiSensei on 2018-08-15
Specify the minute as well.

```
1 1 * * * [etc]
```

runs the script at 1:01 am.

---

### Post by markaurit on 2018-08-16
That did it, thank you!

---

