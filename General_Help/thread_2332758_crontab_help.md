---
title: "crontab help"
date: 2016-08-03
forum: General Help
---

### Post by jaarvidsen on 2016-08-03
hi

i need to run a command/script that runs at:
first bootup, 26th of every month, but only once per month

i know i can use @reboot but then i cant specify a date afaik, and how would i prevent it from running a 2nd time if i should reboot again on the 26th

alternatively is there any other way of achieving this without cron?
any help appreciated

---

### Post by papibe on 2016-08-03
Hi jaarvidsen.

Most of the crontab rules work very well when the machine is pretty much turn on most of the time.

If you use just a 26th rule, it won't run if that day don't turn on the computer. However, if turned on, it would run sometimes later, but definitively after the boot process.

For a complex rule like that, I would use @reboot, and then I'd find out the date on the script itself. For instance, in bash:
```
#!/bin/bash

# obtain current day of the month
current_day="$(date +%d)"

# Exit if it is not the 26th
if [ "$current_day" != "26" ]; then
    exit 1
fi

# actual script
....

```
Hope it helps. Let us know how it goes.
Regards.

---

