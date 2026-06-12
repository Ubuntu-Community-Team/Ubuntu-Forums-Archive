---
title: "Need help with cronjob..."
date: 2007-04-23
forum: General Help
---

### Post by Wiener on 2007-04-23
hello forum,

I have a problem with a cronjob, that should run a small java-application. The application runs well if i start it from the commandline by typing:

java community/cron/Start

I build a little shell-script that is called by the cronjob:
#!/bin/sh

java community/cron/Start

the script is stored under  /var/crons/uploadcron

When I run this script, everything works fine, too.

the script should run once a hour, so I addred the folloeing line to crontab:
00 * * * * /var/crons/uploadcron

this is executed just as defined, but for some reason the application tows an exception when it gets started by the cron:

Exception in thread "main" java.lang.NoClassDefFoundError: community/cron/Start
at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: community/cron/Start
at java.lang.Class.forName(libgcj.so.7)
at gnu.java.lang.MainThread.run(libgcj.so.7)


As I know, this means that classes are not found. But why can does it run well when I start it right away from the shell?

Hope somebody can help....
Wiener

---

### Post by JonnyR on 2007-04-23
Just a hunch, as I came up against the same problem with CRON'd PHP scripts.  Try putting the full path to the java file in your shell script (uploadcron.sh) and let us know if that works for you?

Regards
Jonny.

---

