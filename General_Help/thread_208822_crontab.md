---
title: "crontab"
date: 2006-07-04
forum: General Help
---

### Post by Hotchilli on 2006-07-04
I have set up a crontab with crontab -e 
how to edit it please.

hotchilli

---

### Post by Fac51 on 2006-07-04
cronjobs explained(roughly and maybe a little vague):
```
*     *   *   *    *  command to be executed
-     -    -    -    -
|     |     |     |     |
|     |     |     |     +----- day of week (0 - 6) (Sunday=0)
|     |     |     +------- month (1 - 12)
|     |     +--------- day of month (1 - 31)
|     +----------- hour (0 - 23)
+------------- min (0 - 59)
```


a few examples
```
30 0 1 1,6,12 * = 00:30 Hrs  on 1st of Jan, June & Dec.

0 20 * 10 1-5 = 8.00 PM every weekday (Mon-Fri) only in Oct.

0 0 1,10,15 * * = midnight on 1st ,10th & 15th of month

5,10 0 10 * 1 = At 12.05,12.10 every Monday & on 10th of every month
```

also review the contents of /etc/crontab

---

### Post by Hotchilli on 2006-07-04
thanks for your post very helpful.

hc

---

### Post by lamego on 2006-07-04
man crontab

---

