---
title: "help w/ cron running a simple script"
date: 2006-11-26
forum: General Help
---

### Post by syxbit on 2006-11-26
i'm trying to make an alarm clock.
it should be simple, but for some reason....

i've written a script called "alarm.sh" with this in it.
```

#!/bin/sh
xmms /home/syxbit/Desktop/01.mp3

```

crontab -l shows
02 22 * * * /home/syxbit/Desktop/alarm.sh

to test, it should go off at 10:02PM

i can run the script manually, and it works. it must be a problem with cron

any ideas guys?

---

### Post by rbalfour on 2006-11-26
> **syxbit said:**
> i'm trying to make an alarm clock.
it should be simple, but for some reason....

i've written a script called "alarm.sh" with this in it.
```

#!/bin/sh
xmms /home/syxbit/Desktop/01.mp3

```

crontab -l shows
02 22 * * * /home/syxbit/Desktop/alarm.sh

to test, it should go off at 10:02PM

i can run the script manually, and it works. it must be a problem with cron

any ideas guys?

Have you tried putting in the full path of XMMS?

---

### Post by syxbit on 2006-11-26
hm... don't see why that should matter, as the script works.
still, i tried it, but no change
script now shows
```
#!/bin/sh
/usr/bin/xmms /home/syxbit/Desktop/01.mp3
```

---

### Post by keithweddell on 2006-11-26
Not sure if it will help but have you looked at [this thread]("http://www.ubuntuforums.org/showthread.php?t=185993&highlight=cron")?

Keith

---

### Post by syxbit on 2006-11-26
wow
that fixed it.
for those who are wondering, i changed my crontab to this
09 8 *  * *  export DISPLAY=:0 && /home/syxbit/Desktop/alarm.sh

i'm not sure why, cause it says that "display=:0" is the default, but meh! it worked anyway
thanks a bunch

also, by reading it, i realised i didn't really need a script
i could have it as part of my crontab, like this
```
15 8 *  * *  export DISPLAY=:0 && xmms /home/syxbit/Desktop/01.mp3
```

---

