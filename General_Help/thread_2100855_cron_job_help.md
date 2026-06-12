---
title: "cron job help"
date: 2013-01-03
forum: General Help
---

### Post by sahabcse on 2013-01-03
Hi All

I want to run the script on Tuesdays (On Dates Between 1-7 and 15-21) at 12:00 PM of every month. 

I have tried the below entry, but it is not working proper. Please help

00 12 1-7,15-21 * TUE /root/script.sh

Thanks in Advance
Sahab

---

### Post by rnerwein on 2013-01-03
> **sahabcse said:**
> Hi All

I want to run the script on Tuesdays (On Dates Between 1-7 and 15-21) at 12:00 PM of every month. 

I have tried the below entry, but it is not working proper. Please help

00 12 1-7,15-21 * TUE /root/script.sh

Thanks in Advance
Sahab
hi
why you ain't let decide your script.sh to run or not to run  e.g.:
[ `date +%a` != "Tue" ] && exit 0
echo "it's Tuesday - script will continued"
cheers

---

### Post by conradin on 2013-01-03
cron can be tricky, unless youre deploying a script on multiple computers, I would look at something like this:
[https://apps.ubuntu.com/cat/applications/gnome-schedule/](https://apps.ubuntu.com/cat/applications/gnome-schedule/)

---

### Post by btindie on 2013-01-03
Take a look at "man 5 crontab", specifically the section mentioning
> Note: The day of a command's execution can be specified by two fields —
day  of  month,  and day of week.  If both fields are restricted (i.e.,
aren't *), the command will be run when either field matches  the  cur&#8208;
rent time.  For example,
``30 4 1,15 * 5'' would cause a command to be run at 4:30 am on the 1st
and 15th of each month, plus every Friday. One  can,  however,  achieve
the  desired result by adding a test to the command (see the last exam&#8208;
ple in EXAMPLE CRON FILE below).

> # Run on every second Saturday of the month
0 4 8-14 * *    test $(date +%u) -eq 6 && echo "2nd Saturday"

So you'd probably want something like
> 0 12 1-7,15-21 * * [ $(date +%u) -eq 2 ] && /root/script.sh

---

