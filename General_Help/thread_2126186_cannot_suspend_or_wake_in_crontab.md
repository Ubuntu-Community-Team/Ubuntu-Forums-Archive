---
title: "cannot suspend or wake in crontab"
date: 2013-03-16
forum: General Help
---

### Post by qwertyjjj on 2013-03-16
I put this in crontab but it will not trigger the command:

33 12 * * * dbus-send --system --print-reply     --dest="org.freedesktop.UPower$

I tried rtcwake as well and that doesn't work eiuther.

---

### Post by sudodus on 2013-03-16
I think you should be able to suspend, but not wake up from a cron job.

But the environment of cron is very simple, no path, no environment variables, (or at least very reduced compared to bash in the terminal window). So you need to enter the full path to all commands and file names. Check with ```
which  dbus-send
``` In my computer the full path is
```
/usr/bin/dbus-send
```

Also, if you need sudo, you should use ```
sudo crontab -e 
```(and no sudo inside it).

---

