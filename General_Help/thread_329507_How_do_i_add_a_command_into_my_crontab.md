---
title: "How do i add a command into my crontab"
date: 2007-01-01
forum: General Help
---

### Post by CameronCalver on 2007-01-01
hello i am trying to add a command into my crontab
i want it to run this .sh file at 11:30 am every day i tryed
```
30 11 * * * * /home/cameron/experimental/backup/backuo,sh 
```
but it said  ```
cameron@ubuntu:~$ crontab -e
no crontab for cameron - using an empty one
crontab: installing new crontab
"/tmp/crontab.4Lpq3C/crontab":1: bad command
errors in crontab file, can't install.
Do you want to retry the same edit? 
```

my whole crontab was 
```
# m h  dom mon dow   command
30 11 * * * * /home/cameron/experimental/backup/backuo.sh
 
``` and it wont let me save it so yeh does anyone no how to fix

---

### Post by bruenig on 2007-01-01
is it backuo.sh or backup.sh

---

### Post by CameronCalver on 2007-01-01
backup.sh lol but stil

---

### Post by raul_ on 2007-01-01
[http://www.ubuntuforums.com/showthread.php?t=74197&highlight=prelinking]("http://www.ubuntuforums.com/showthread.php?t=74197&highlight=prelinking")

See section 6...i think that's what you want? :-k

---

### Post by bruenig on 2007-01-01
> **CameronCalver said:**
> backup.sh lol but stil

Well that could explain the bad command error.

Oh and the prelinking thing, that doesn't seem to me to be what you are doing, but maybe I am wrong.

---

### Post by CameronCalver on 2007-01-01
well i decided to use kcron so its all good now

---

### Post by Pluk on 2007-01-01
For future reference, since you've already found an alternative solution :)

> **CameronCalver said:**
> 

```
# m h  dom mon dow   command
30 11 * * * * /home/cameron/experimental/backup/backuo.sh
 
``` 

In cron there should be 5 entries for the time a command should run:
minute 0-59
hour 0-23
day of month 1-31
month 1-12 (or names, see below)
day of week 0-7 (0 or 7 is Sun, or use names) 

You have tried to add a 6th (* * * * instead of * * *)

---

### Post by ThanhBT on 2008-05-03
Change it to
```
30 11 * * * /home/cameron/experimental/backup/backuo.sh
```
3 * symbol not 4

---

