---
title: "Scheduled Commands"
date: 2013-02-01
forum: General Help
---

### Post by linuxvstheworld on 2013-02-01
In a script, can I tell a command to execute at a certain time?

---

### Post by omeomi on 2013-02-01
You can use cron jobs for that. This might be useful: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by The Cog on 2013-02-01
For one-off commands, you can use **at**, like this:
```
echo DISPLAY=:0.0 xeyes | at 13:19
```

---

