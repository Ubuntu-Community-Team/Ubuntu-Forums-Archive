---
title: "at command"
date: 2020-09-05
forum: General Help
---

### Post by T6&amp;sfpER35% on 2020-09-05
i'm trying to use the at command to shutdown pc at a certain time.
i tested it but it's not working

```
o14@01:~$ at 23:05
warning: commands will be executed using /bin/sh
at> shutdown
at> <EOT>
job 4 at Sat Sep  5 23:05:00 2020
o14@01:~$ 



```

23:05 will come and nothing would happen...what am i missing?

---

### Post by Impavidus on 2020-09-06
Permissions? If I'm not mistaken, shutdown requires root permissions. There's an exception for shutdowns triggered by the user currently logged in if that's the only (human) user at that moment, but maybe that's not properly detected when using it via at.

BTW, shutdown accepts a time argument. Without the time argument is will shutdown one minute after invocation (so that's at 23:06 in your command; did you wait long enough?), but you can specify an exact time:```
shutdown 23:05
```

---

### Post by T6&amp;sfpER35% on 2020-09-06
ok after a bit of search i see i must use the shutdown command ,not the at command.
my problem is ,with shutdown command you apparently can only specify a time ,not a date and time?is that correct?

---

### Post by ajgreeny on 2020-09-06
What about using **cron** instead of **at**?

That will let you choose date and time easily, anything up to a year from the current time.

---

### Post by dinkidonk on 2020-09-06
You can specify an amount of minutes to elapse before shutdown, eg. "sudo shutdown +10" = shut down in 10 minutes. You should still be able to use the "at" command, but it must be sudo'ed for shutdown to work.

---

### Post by T6&amp;sfpER35% on 2020-09-07
thanks for all the input guys
found that **sudo at .....**works just fine 
;)

---

### Post by TheFu on 2020-09-07
You can also feed at commands in from stdin.
```
$ echo "sudo shutdown" | at 23:05 fri
```

When I post files for people, I'll often say - you have 7 days to grab this file at [https://.](https://.)......... .  After that time, it will be automatically removed.  Then I run **echo "rm ./file-for-Joe" | at now + 7 days**.  

I do the same with files that I need to keep for 60 days, but no longer.  For example, we have to have vehicle emission test performed where I live and provide that paperwork with the annual vehicle registrations.  So, I scan the file, since the mail can lose stuff and I'd be forced to pay again to get another test if I couldn't print a copy.  But once the registration proof and sticker gets returned, those files are useless.  If I mail stuff in for the govt, I'll keep a copy for some time as proof, but pretty much anything that isn't taxes, is a short-term document for me - keep 60 days, no longer.

When I changed backup tools years ago, I didn't want to immediately delete the old backups. I wanted at least 30 days under the new system, but the storage used by the old system shouldn't be left around for me to remember to clean up later.  'at' to the aid.

Since January, I've been use **at** to schedule recording broadcast TV with a wget script that "records" from network tuners. The entire process is complex, but the use of it today is about 3 commands per week regardless of the number of shows to be recorded. Takes about 30 seconds, a week, total time. Basically, I have scripts that build scripts. All because $0 is better than $35/yr to me. In N. America, TV schedules aren't free.  

```
echo "/home/thefu/bin/tv-record.sh 46.1 66 Bull-r" | at 21:57 mon
echo "/home/thefu/bin/tv-record.sh 8.1 66 Frontline-Poor_in_America" | at 20:57 tue
echo "/home/thefu/bin/tv-record.sh 69.1 66 The_100-S7E13" | at 19:57 wed
echo "/home/thefu/bin/tv-record.sh 8.1 126 NOVA-Human_Nature" | at 22:57 wed  
echo "/home/thefu/bin/tv-record.sh 2.1 186 College_Football-TBD" | at 11:57 sat
```

You get the idea.  If anyone is using 'at' to do batch stuff, there are better tools. There is a 'batch' command, but I prefer taskspooler, tsp. That's a completely different question.  I suppose I could have cron check a specific file every 10 minutes to decide if a show needs to be recorded out of the text DB that builds those commands.  Hummm.  I have an itch. ;)

---

### Post by dinkidonk on 2020-09-08
> **TheFu said:**
> You can also feed at commands in from stdin.
```
$ echo "sudo shutdown" | at 23:05 fri
```

I'm quite sure that's not gonna work. When "sudo shutdown" is executed by "at", which is running at user-level, the system will ask for a password causing the "at" command to hang or fail.

---

### Post by Impavidus on 2020-09-08
Indeed, unless sudo has been configured to allow the shutdown command by this user without password. It's possible to configure sudo this way.

---

### Post by TheFu on 2020-09-08
> **Impavidus said:**
> Indeed, unless sudo has been configured to allow the shutdown command by this user without password. It's possible to configure sudo this way.

Exactly. One of the first things I setup are a select subset of commands for my userid to run without password prompts in the sudoers, just after purging nano. ;)

Sorry that I forgot to mention that aspect.  Also, I don't trust the PATH, so it would be /sbin/shutdown in my script.

---

