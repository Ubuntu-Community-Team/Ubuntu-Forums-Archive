---
title: "Crontab job help"
date: 2024-09-25
forum: General Help
---

### Post by raleigh3 on 2024-09-25
The crontab generator sites are helpful, but there are some cron jobs that they can not generate.

I need help with getting this to run every two weeks. And will it run if my computer is not on?

```
#!/bin/bash
#----------------------------------------------------------------------------
# SatDiskMessage.sh
# Help from raj
#----------------------------------------------------------------------------
# echo $XDG_RUNTIME_DIR
# /run/user/1000

export XDG_RUNTIME_DIR=/run/user/1000

/usr/bin/notify-send --expire-time=5000 "Water Dirt under satellite dish !!!"
```

---

### Post by TheFu on 2024-09-25
Cron will only work if your computer is on at the specific time.  If you want the task to run later the same day, even if it isn't on at the time, use anacron instead.

The way to address running a job every other week is to run it every week, but at the top of the invoked script, check if the week is even or odd using the week of the year count.  Then either exit immediately or continue on.
Also, trying to interact with a GUI from cron is a mistake.  Instead, use the built-in capability that will send an email.

This is what I mean by the count of the week in the year:

```
$ date "+%V"
39
```

So, this is week 39 of 52 in 2024.  [https://www.epochconverter.com/weeknumbers](https://www.epochconverter.com/weeknumbers)
Handy to think in this way, right?

I do something similar, just using days of the month instead, to determine when to run SMART long and short tests.  I run long tests the first week of the month (any days in the month less than 8), otherwise, I run short SMART tests.  Inside the script, I have this code:
```
# ########################################################
# Short or long test?
if [ $(date +%d) -lt 8 ] ; then
   TEST_TYPE="long"
else
   TEST_TYPE="short"
fi
```

The crontab file looks like this:
```
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR # sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  command to be executed
# *  *  *  *  *  command --arg1 --arg2 file1 file2 2>&1
# m h  dom mon dow   command
9 5 * * 2 /usr/local/sbin/smart_info
```
I put those comments in every crontab as a reminder for what each field means.
So, that script is run every Tuesday at 5:09am.  On completion, the output is emailed to the root account on the system, which I have setup to forward to my email account on my mail server.
About 5:15am yesterday, I received a text email of about 30.7K with all the output from the SMART tests for all disks on the system.  I also write those results to specific files in a specific directory on the system to be available to comparisons.  SMART data is best used over time to see the trajectory of any issues. I keep 6 months of those test files. Sometimes disks get 1 or 2 errors, but then those sectors are reallocated and never a problem again for the next 10 yrs.  Other times, the errors get consistently worse every test until the disk fails a few days-weeks later. In April, I had an 8 month old drive die quickly. I've posted the SMART test changes for it in these forums, if you are interested in seeing a disk fail quickly.  It was a 5 yr warranty WD-Black HDD that failed. WD took about a month to replace it through their RMA process.  When I posted the SMART data, they never asked any other questions before approving the RMA.

---

