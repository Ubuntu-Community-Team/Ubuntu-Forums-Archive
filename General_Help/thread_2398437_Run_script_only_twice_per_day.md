---
title: "Run script only twice per day"
date: 2018-08-12
forum: General Help
---

### Post by raleigh3 on 2018-08-12
Can I run a script no more than twice a day without using cron?

Maybe create a file when script is first run and check its date?

---

### Post by TheFu on 2018-08-12
yes.
yes.

Perhaps 2 a self-renaming scripts that is based on the date?  The last thing it does is rename itself to match tomorrow's date.  Call the script based on the date.  You can have a controlling script that sleeps for seconds, minutes, hours between attempts.  You asked a question yesterday about getting formatted dates ... use that.  Probably easiest to deal with Julian dates, then only once a year would the overflow happen.

ABSG ...

Why the hate for cron?

---

### Post by raleigh3 on 2018-08-12
I find cron a little too complex.

I tried looking for a front end for it.

---

### Post by TheFu on 2018-08-13
Cron isn't hard.  The file format makes since once you "get" it.  
[https://crontab.guru/](https://crontab.guru/) explains a crontab entry.  Use **crontab -e** to access the editor for your account crontab. If you want to access the root crontab, use **sudo crontab -e**.

Put this into every crontab as comments:
```
# *     *     *   *    *        command to be executed
# -     -     -   -    -
# |     |     |   |    |
# |     |     |   |    +----- day of week (0 - 6) (Sunday=0)
# |     |     |   +------- month (1 - 12)
# |     |     +--------- day of month (1 - 31)
# |     +----------- hour (0 - 23)
# +------------- min (0 - 59)
```
Replace the * with a number for what you want.  Whitespace is the field separator.
Twice a day, we need to pick an hour AND min to run. It will run every day of the week, every day of the month, every month of the year,   Each * is an "AND" - use a comma to make a field into an "OR".
```
16 6,18 * * * /path/to/command
```
That will run at 6:16 and 18:16 daily, every day of the week, every day of the month, every month of the year. Simple. [http://www.adminschoice.com/crontab-quick-reference](http://www.adminschoice.com/crontab-quick-reference) has more examples which are useful for learning.

---

### Post by raleigh3 on 2018-08-13
Thanks, I put it in my crontab.

It's not so hard now. :-)

---

