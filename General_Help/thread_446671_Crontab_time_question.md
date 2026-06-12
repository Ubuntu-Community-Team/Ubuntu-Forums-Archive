---
title: "Crontab time question"
date: 2007-05-17
forum: General Help
---

### Post by lifeempowered.com on 2007-05-17
Hey does anyone know what the following crontab time would translate into in real time?

0 * * * *    /whatever/script/something.pl >> whatever.log

Thanks in advance!

---

### Post by fanatik on 2007-05-17
it would run every hour of every day on the hour, ie 1pm, 2pm, 3pm..... etc.

```
####################################################################
#minute (0-59),                                                    #
#|      hour (0-23),                                               #
#|      |       day of the month (1-31),                           #
#|      |       |       month of the year (1-12),                  #
#|      |       |       |       day of the week (0-6 with 0=Sunday)#
#|      |       |       |       |       commands                   #
####################################################################
0       *       *       *       *       /whatever/script/something.pl >> whatever.log
```

---

