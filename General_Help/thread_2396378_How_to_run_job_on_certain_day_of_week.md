---
title: "How to run job on certain day of week"
date: 2018-07-14
forum: General Help
---

### Post by Ralph L on 2018-07-14
I have 2 separate backup tasks that I want to run--the first every Monday, the second every Thursday.  I want to use anacron so that if the computer is down during the scheduled day, the job will run ONCE the next time the computer is running.  Looking at [https://www.digitalocean.com/community/tutorials/how-to-schedule-routine-tasks-with-cron-and-anacron-on-a-vps](https://www.digitalocean.com/community/tutorials/how-to-schedule-routine-tasks-with-cron-and-anacron-on-a-vps) and the anacron man page, I don't see how to do this.  Anacron does not seem to have a parameter to specify day of week.  I am pretty sure that I can do this with fron, but I wanted to avoid the hassle of installing it, and learning to use it.

Any help appreciated.

---

### Post by TheFu on 2018-07-14
Any help?

I think anacron will only run a task once a day with any guarantee.  So, if you insist on using it, then you will need to script the other limiting aspects yourself.  Date and DoW calculations are well known in the scripting world.  Linux is extremely flexible, but it is up to the admin/user to provide some of that if a tool doesn't handle it already.

Seems a better backup tool is needed to me.   
I'd run either weekly or daily backup jobs?  

I run daily backups and retain between 60 and 120 days, depending on the system.  No complex rules are needed, because the backup tool is efficient.  For most of my systems, backups take 2-3 minutes a day.  If the source is 20G, then 60 days of daily backups uses about 23G.  The storage amount depends on how much data changes from day to day, of course. No need for complex backup techniques, just use a better backup tool.

---

### Post by Ralph L on 2018-07-17
Thanks for the response.  I think the first thing I will do is try to get fcron working again.  I used it a few years ago, and it seemed to have the features I am looking for plus a number of others that could be useful in the future.  However, I am already running into problems.  I can't download the USA version from [http://fcron.free.fr/download.php](http://fcron.free.fr/download.php).  It says "Unable to connect".  I can connect to the french version, but I have yet to try it, and don't know what kinds of problems I would have.  I sent an email to Thibault Godouet, at <fcron@free.fr> , but haven't heard back.

Thanks again....

---

### Post by Ralph L on 2018-07-28
This site tell how to run fcron/fcronq:  [https://ubuntuforums.org/showthread.php?t=2396979](https://ubuntuforums.org/showthread.php?t=2396979).  It does the job of running on a certain day of week.

---

### Post by TheFu on 2018-07-28
> **Ralph L said:**
> This site tell how to run fcron/fcronq:  [https://ubuntuforums.org/showthread.php?t=2396979](https://ubuntuforums.org/showthread.php?t=2396979).  It does the job of running on a certain day of week.

cron has the ability to run on a specific day of the week or a specific day of the month and at specific times.   That wasn't the question from the OP.

```
# m h  dom mon dow   command
where
m = 0-59  (*/5 will match every 5 minutes, 0,5,10,15,20, .... 55.  */15, */1 are also popular)
h = 0-24  (*/2 will match every even hour;  if you want to run a 6,10,14,18,20 hrs, you can)
dom = 1-31  (if you choose 31, only months with 31 days will run the job)
mon = 1-12 (Jan/Feb/.... can also be used)
dow = 0-7 (0 and 7 are Sunday, 1=Mon, 2=Tue ... )
Ranges can be used for each except m and h.  Those can use lists or divisors. Spaces are the field separator.
```

So if you want to run a job a 3:04 am only on the 2nd Tuesday, then you'd have
```
4 3 8-14 * 2  /path/to/job
```
It is fairly powerful, but if the computer isn't on a 3:04am on the 2nd Tuesday, then the job won't be run. 

When using cron, I avoid running tasks on the 1st of the month or at 5 min increments or at the top of the hour. Automatically installed tasks will pick those times.

---

