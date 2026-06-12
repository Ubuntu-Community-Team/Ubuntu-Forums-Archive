---
title: "Create a script that repeats every 25 minutes"
date: 2016-05-24
forum: General Help
---

### Post by simone22 on 2016-05-24
Hi, I need a scrip that repeats some commands every 25 minutes, I have seen many guides around but what I need is something slightly different: I need that the script starts to run when I start up the computer, and then from that point I want that it repeats every 25 minutes.
I was thinking to put in in the local.rc file, is it possible? thank you in advance.

---

### Post by jeremy31 on 2016-05-24
Putting it in rc.local won't work the way you want, [cron](https://help.ubuntu.com/community/CronHowto) is likely what you want

---

### Post by Habitual on 2016-05-24
Cron
```
*/25 * * * * /path/to/script.sh
```

---

### Post by nerdtron on 2016-05-25
I don't think the rc.local is working on Ubuntu 16.04. It seems erratic on my system. And I recommend a cron job for this. 

Create the script, and better to use absolute filenames/path on the commands.
Make the script executable:
```
sudo chmod a+x /folder/script.sh
```

Then edit the crontab:
```
crontab -e
```

Add a line to execute it on startup:
```
@reboot /bin/bash /path/to/script.sh
```

Line to execute every 25 minutes:
```
*/25 * * * */bin/bash /path/to/script.sh
```

---

### Post by simone22 on 2016-05-25
> **nerdtron said:**
> I don't think the rc.local is working on Ubuntu 16.04. It seems erratic on my system. And I recommend a cron job for this. 

Create the script, and better to use absolute filenames/path on the commands.
Make the script executable:
```
sudo chmod a+x /folder/script.sh
```

Then edit the crontab:
```
crontab -e
```

Add a line to execute it on startup:
```
@reboot /bin/bash /path/to/script.sh
```

Line to execute every 25 minutes:
```
*/25 * * * */bin/bash /path/to/script.sh
```

Interesting thank you. Rc.local is in Ubuntu 16.04 and for me it works, the reason why I need this script is actually for setting 3 power saving options that regularly go off when I hibernate my laptop or I pass from battery to Ac or viceversa.
So I though that the only way to regularly make sure that those options are enabled is to use a script like this that periodically repeats this 3 power saving commands (got them from power top).

Last question, why do you use the command @reboot in the crontab edited file? Does it mean that the script will be executed also every startup of the system ?

---

### Post by nerdtron on 2016-05-25
> **simone22 said:**
> 

Last question, why do you use the command @reboot in the crontab edited file? Does it mean that the script will be executed also every startup of the system ?

Yes, correct. You may be familiar with crontab which uses the five fields to declare the minute, hour, day of month, month, and weekday, as seen from the examples above.

Crontab also understands special words like the ones listed below:
```
@reboot     Run once, at startup
@yearly     Run once  a year     "0 0 1 1 *"
@annually   (same as  @yearly)
@monthly    Run once  a month    "0 0 1 * *"
@weekly     Run once  a week     "0 0 * * 0"
@daily      Run once  a day      "0 0 * * *"
@midnight   (same as  @daily)
@hourly     Run once  an hour    "0 * * * *" 
```

---

### Post by simone22 on 2016-05-25
> **nerdtron said:**
> Yes, correct. You may be familiar with crontab which uses the five fields to declare the minute, hour, day of month, month, and weekday, as seen from the examples above.

Crontab also understands special words like the ones listed below:
```
@reboot     Run once, at startup
@yearly     Run once  a year     "0 0 1 1 *"
@annually   (same as  @yearly)
@monthly    Run once  a month    "0 0 1 * *"
@weekly     Run once  a week     "0 0 * * 0"
@daily      Run once  a day      "0 0 * * *"
@midnight   (same as  @daily)
@hourly     Run once  an hour    "0 * * * *" 
```

Thanks! so kind of you.

---

### Post by vasa1 on 2016-05-25
You can mark your thread **SOLVED**. Visit [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) to know how and why we all benefit. You could also specify the response or responses that provided the solution in a new post in the same thread. That would be even more helpful to those who come by later!

---

### Post by Impavidus on 2016-05-25
> **nerdtron said:**
> 
Line to execute every 25 minutes:
```
*/25 * * * */bin/bash /path/to/script.sh
```

That will run the script whenever the clock reads a multiple of 25 minutes after the hour, so at 0:00, 0:25, 0:50, 1:00, 1:25, 1:50, 2:00 etc. Not exactly what I call every 25 minutes. That only works in a single line if it has to run an integer number of times per hour. Else, you need 5 lines in your crontab file with the correct hour/minute combinations (which will still jump at midnight with a 15 minute interval) or run the script every 5 minutes and have it check whether it's a multiple of 25 minutes and if not exit. Easier to run the script every 20 or 30 minutes, if that doesn't matter too much.

---

