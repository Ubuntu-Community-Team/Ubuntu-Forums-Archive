---
title: "Can't get cron daemon running in feisty"
date: 2007-05-26
forum: General Help
---

### Post by pyjamashark on 2007-05-26
Hi I'm a newbie and desperately need some help in Ubuntu Fesity,
I've written a small backup script and have edited my crontab file correctly to run it at a certain time. However, when  I look under System > Administration > Systems Monitor, the cron daemon isn't there and the option to run it isn't there either. When I type cron on the command line it gives me an error message. Anacron does register as running but I can't find any decent how-to's to tell me how I can program it to run my script automatically when I want.
Please help,
thanks 
Joe

PS.
This is in my crontab file
55 22 * * *     ./home/pyjamashark/backupscript

I have made that script executable too.
The script works perfectly when executed from the command line.

---

### Post by Bachstelze on 2007-05-26
Remove that dot before the path of the file.

---

