---
title: "Crontab Log Script"
date: 2007-11-21
forum: General Help
---

### Post by bbarcelo on 2007-11-21
I've got some logs that have identifying strings in and are updated daily. I want to have a crontab script run daily at some time to parse the log, identify the string and the text after it, and write to a directory with the current date as the filename. I've been messing around with it, but have only gotten as far as getting the command to create the file with today's date. Here's what I've got:
```
28 17 * * * grep -ie "`date --rfs-3339=date`.*String\b*here" "/home/user/.logdir/logs/logs-file name-log#-string.log" > ~/.parsedlogs/`date --rfs-3339=date`.txt
```

The log file being parsed has a timestamp that looks like this (with the string identifier after it):
[17:20:34 2007-11-21](Name)     String: text

I don't want the script to generate more files on top of itself, and I don't want it grabbing things after the identifier if they happened on a previous day. Since I've only got one log file, I want this script to separate things after the identifier into separate log files without duplicates.

So, I'm a bit stuck, and also a bit new to crontab (and somewhat new to Linux, but not a complete newb). Any help getting this to work is appreciated and I'll try to answer all questions quickly and accurately.

---

### Post by cmnorton on 2007-11-21
Wouldn't it be easier if  you put that command in a shell script file, set the executable permissions, and then pointed to that newly-created shell script file directly? Then you could test the command outside the cron environment.

---

### Post by bbarcelo on 2007-11-21
Well I can still test it out if I just grab the command, but it gives me the same errors, so I just posted the entire thing.

---

