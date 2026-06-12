---
title: "date and time"
date: 2016-06-13
forum: General Help
---

### Post by hmiersch on 2016-06-13
hi.

today i noticed that the time and date are no longer displayed in my menu bar. so i went into system settings and clicked on time & date. after logging in and clicking the clock tab, i had quite a surprise: the show clock in menu bar option is ticked, and ALL options are greyed out, so i can't change anything.

so the question is, what's going on here? have i done something wrong? has something gone haywire? i dont know what to do about this :-(

---

### Post by X-RED_Tech on 2016-06-13
Is it in regular Ubuntu or in a variant with a different desktop environment?

---

### Post by hmiersch on 2016-06-14
It's standard Ubuntu 14.04, kept up to date using the software updater.

---

### Post by vanadium on 2016-06-14
This is probably the "indicator-datetime or -session missing ~10% of the time" bug, which I think was never really solved in 14.04 and even later versions. (No problems anymore in 16.04). With the command "killall unity-panel-service", you will have your indicator back. To prevent the issue from bothering me, I added the following command to Startup applications (you will need to repeat this for each user account):
```

sh -c "sleep 0.4 && killall unity-panel-service"

```
This would make sure that the indicator would be available at each login.

---

