---
title: "cron every minute"
date: 2007-10-22
forum: General Help
---

### Post by md5hash on 2007-10-22
how can i setup a timer that would execute something every minute

---

### Post by mahousaru on 2007-10-22
crontab -e

then set a tab like

* * * * * /command

The first star is the minute section, so having a star there will execute every minute

In case it makes it more clear if you wanted every 5 mins then it would be

*/5 * * * * /command/to/execute

And the other stars are from left to right

minute hour dayofmonth month dayofweek* 

*0=sunday

---

### Post by md5hash on 2007-10-22
cool thanks alot hehe

---

