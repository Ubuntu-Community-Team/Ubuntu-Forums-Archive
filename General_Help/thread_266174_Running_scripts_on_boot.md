---
title: "Running scripts on boot"
date: 2006-09-26
forum: General Help
---

### Post by bforbes on 2006-09-26
I need to run this script each time my computer boots up:

```

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11"

```

What is the best way to do that?

---

### Post by whizbaby on 2006-09-26
cron
[http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)
EDIT:
hint - use **@reboot** as time specification.

---

### Post by bforbes on 2006-09-27
That doesn't seem to be the right place to run xmodmap. I confirmed that everything in the crontab is running, but nothing seems to happen for xmodmap. Is there another place I can try, like some sort of startup script?

---

### Post by yopnono on 2006-09-27
Try /etc/rc.local

---

### Post by ayoli on 2006-09-27
the best way to run your script/command at boot is putting it in /etc/rc.local before *exit 0*

---

### Post by bforbes on 2006-09-27
I put it in /etc/rc.local, it doesn't seem to be running. I put a "touch ~/foo" in as well, that didn't run. But there is /etc/rc2.d/S99rc.local which points to /etc/init.d/rc.local, which should call /etc/rc.local. Why wouldn't it do that?

EDIT: I confirmed that /etc/init.d/rc.local runs. I just don't know why it's not running /etc/rc.local. I guess I could just put the code in /etc/init.d/rc.local. Hopefully xmodmap works there.

---

### Post by yopnono on 2006-09-27
The script is running as root so this "touch ~/foo" would end up in the root dir.

---

### Post by dcstar on 2006-09-27
> **bforbes said:**
> I need to run this script each time my computer boots up:

```

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7 10 11"

```

What is the best way to do that?

Put in the full path to the program - commands **not** run in a user command shell do not have the benefit of a path being set.

Use:
```
locate xmodmap
``` to find the full path.

---

### Post by ayoli on 2006-09-27
> **dcstar said:**
> Put in the full path to the program - commands **not** run in a user command shell do not have the benefit of a path being set.

Use:
```
locate xmodmap
``` to find the full path.
which is even better to find application path:
```
$ which xmodmap
/usr/bin/xmodmap
```

---

### Post by beerorkid on 2006-09-27
why not system --> prefferences --> sessions --> startup programs ?

1/2 dozen of one 6 of the other I guess

---

### Post by skymt on 2006-09-27
AFAIK, xmodmap needs a running X server, so putting it in rc.local will not work. You should add the command to the startup items tab in GNOME session properties, so it will run on login.

---

### Post by ayoli on 2006-09-27
> **skymt said:**
> AFAIK, xmodmap needs a running X server, so putting it in rc.local will not work. 
you're right, btw gdm script is supposed to be launched before rc.local, so maybe he should specify the display.
on the other hand:
> **skymt said:**
> You should add the command to the startup items tab in GNOME session properties, so it will run on login.
seems a nice alternative :)

---

### Post by bforbes on 2006-09-28
What about in KDE?

---

### Post by bforbes on 2006-09-30
I have succeeded, by running the script from the KDE Autostart folder, as per these instructions: 

[http://www.kde.org/areas/sysadmin/startup.php#kdesktop](http://www.kde.org/areas/sysadmin/startup.php#kdesktop)

---

