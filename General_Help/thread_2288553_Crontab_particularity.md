---
title: "Crontab particularity"
date: 2015-07-28
forum: General Help
---

### Post by tony86 on 2015-07-28
Hi all

I need some insight with crontab which I'm using to call a shell every 2nd day of each month.
However if this date falls on a Saturday or Sunday then we need to make sure that the execution is on the subsequent Monday.

Is this possible?

Thanks

Tony

---

### Post by slickymaster on 2015-07-28
*Moved to the ***General Help*** sub-forum*

---

### Post by ian-weisser on 2015-07-28
It's not directly possible using cron logic. Cron doesn't know about conditions and can't do calendar logic. It simply runs what it's told to run at a certain time.
However, it's easily possible using any of several intermediate steps.

For example, one way using an intermediate 'at' job:
1) Cron.monthly job that does the calendar logic (a script) and sets an at job (see 'man at') for the correct date/time.
2) The at job calls your shell.

Many other ways to do it.

---

### Post by tony86 on 2015-07-28
Hello Ian

Thanks for that. I'm not sure that I understood you correctly though.
The 'at' job will decide the date/time - so far so good - so I'd set the 'at' for every 2nd day of the month.
However if this is a Saturday/Sunday, how do I convey that day should be day+1?

Once this is determined then I understand that the 'at' job will call my shell.

Currently what I have in my cron file is:

00 08 2 * * ./TEST.ksh

Can you please give me more details?

P.S. I admit that I'm a linux novice

---

### Post by Lars Noodén on 2015-07-28
You could have cron call a script on the second day of the month.  That script can then test if is a Saturday, Sunday or weekday.  If it is a weekday, it runs your original script right away.  If it is a Saturday, it calls [at](http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html) to run the original script at "now +2 days".  If it is a Sunday, it calls [at](http://manpages.ubuntu.com/manpages/trusty/en/man1/at.1.html) to run the original script at "now +1 day".

```

echo /usr/local/bin/myscript | at now +2 days

```

---

### Post by ian-weisser on 2015-07-28
One imagines if the 1st is Saturday, then you want the job for 'at now + 2 days'
If the 1st is Sunday, then you want the job for 'at now + 1 day'

How do you determine the day of the week? Use a script with the 'date' command. See 'man date'.

For example:
```
$ date -u +%u
2      ## Using %u, Monday is 1, Sunday is 7. Today is Tuesday.



## Let's use Tuesday in a simple one-line if/then script.
## You can try this at any shell prompt.

$ if [ $(date -u +%u) -eq 2 ]; then echo "It's Tuesday"; else echo "It's not Tuesday"; fi
It's Tuesday



## Here's a more familiar way to script the same thing. Save the script and make it executable.

#!/bin/sh
if [ $(date -u +%u) -eq 2 ]
then
  echo "It's Tuesday"
else
  echo "It's not Tuesday"
fi
exit 0
```

Write a script that creates the at job.
Place the script in /etc/cron.monthly

Cron will run the script on the first of each month.

---

### Post by SeijiSensei on 2015-07-28
I suggest having the script write a timestamp to a file each time it is run.  Add a cron entry for a script that runs every Monday, checks the date on the file, and runs the original script if needed.

---

