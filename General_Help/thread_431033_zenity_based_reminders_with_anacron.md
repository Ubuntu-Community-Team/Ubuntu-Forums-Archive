---
title: "zenity based reminders with anacron"
date: 2007-05-02
forum: General Help
---

### Post by timmie on 2007-05-02
Hello,
following [crontab: How to run GUI programs with cron](http://ubuntuforums.org/showthread.php?p=1077195#post1077195) I created a script to remind me of my daily, weekly backups to a external disk.

I want to use **Zenity ** to show a notifigation in the Gnome Panel notification area.

Here's the script I use:
```

#!/bin/bash
export DISPLAY=:0.0
zenity --notification --text='Don't forget your daily backup' 

```

I saved this in a file named *backup-reminder_daily_zenity* and placed it in  */etc/cron.daily*.

But nothing happens.

If I test my cron-scripts with
```
sudo nice run-parts -v /etc/cron.daily
``` it runs well. It also works when I use my personal crontab edited with ```
~$: contab -e
```.

Only with the daily anacron it doesn't work.

Do you have any suggestion how I can get this work?

---

### Post by flyingbrass on 2007-05-02
I think the problem is root doesn't have access to your X session.  See [this thread](http://ubuntuforums.org/showthread.php?t=285985).

---

### Post by timmie on 2007-05-02
Yes, you are right:

```

root:/etc/cron.daily# sh backup-reminder_daily_zenity 
root:/etc/cron.daily# Xlib: connection to ":0.0" refused by server

```

After reading many forum posts I con cnclude that this is something linux doesn't handle due to the restrictions in access to X for root...

Strange that there's no simple way to get this done.

---

### Post by dcstar on 2007-05-02
> **timmie said:**
> Hello,
following [crontab: How to run GUI programs with cron](http://ubuntuforums.org/showthread.php?p=1077195#post1077195) I created a script to remind me of my daily, weekly backups to a external disk.

I want to use **Zenity ** to show a notifigation in the Gnome Panel notification area.

Here's the script I use:
```

#!/bin/bash
export DISPLAY=:0.0
zenity --notification --text='Don't forget your daily backup' 

```

I saved this in a file named *backup-reminder_daily_zenity* and placed it in  */etc/cron.daily*.

But nothing happens.

If I test my cron-scripts with
```
sudo nice run-parts -v /etc/cron.daily
``` it runs well. It also works when I use my personal crontab edited with ```
~$: contab -e
```.

Only with the daily anacron it doesn't work.

Do you have any suggestion how I can get this work?
Try:
```
**/usr/bin/**zenity --notification --text='Don't forget your daily backup' 
```

---

