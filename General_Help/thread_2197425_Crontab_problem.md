---
title: "Crontab problem"
date: 2014-01-03
forum: General Help
---

### Post by jordan9 on 2014-01-03
[SIZE=2][FONT=arial]Hi,
I have created a cronjob with a command I know to work in the terminal, however, it does not work when executed in cron.
I have placed this job in the prompt provided by crontab -e.

Code:[/FONT][/SIZE]

[FONT=Menlo]*/1 * * * * /usr/bin/python -c 'import script; script.checkEmail()'[/FONT]
[FONT=arial]
[SIZE=2]However, it does not complete. I have other jobs in this file which execute fine.
Any help would be greatly appreciated.
Regards.

[/SIZE][/FONT][FONT=arial][SIZE=2][FONT=arial](P.S, please note that this command will not work in the terminal if I prefix script (the file) with it's address (/var/www/RA))
[/FONT][/SIZE]
[/FONT]

---

### Post by papibe on 2014-01-03
Hi jordan9. Welcome to the forum ):P

crontab has a very limited environment, so you may need to set some environment variables.

I'm not familiar with the 'script' module, and its function checkEmail(). If it opens anything from the GUI, you just may need to define DISPLAY. For instance:
```
*/1 * * * * **DISPLAY=:0** /usr/bin/python -c 'import script; script.checkEmail()'
```
Hope it helps. Let us know how it goes.
Come here often and have fun.

Regards.

---

### Post by jordan9 on 2014-01-10
Wonderful, thank you!

---

