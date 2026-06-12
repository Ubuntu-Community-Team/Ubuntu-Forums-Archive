---
title: "[SOLVED] anacrom vs atd"
date: 2007-04-02
forum: General Help
---

### Post by El_Matthews on 2007-04-02
Hello,

maybe this is a stupid question but are anacron and atd not doing the same thing ?

if yes, do we need them both on a pc ?

---

### Post by snifer on 2007-04-20
AFAIK, anacron executes scripts in /etc/cron.{daily,hourly,monthly,weekly}, so it won't be a good idea to disable it.
On the other hand, atd execute jobs in /var/spool/cron/atjobs (empty in my pc).

---

### Post by stylishpants on 2007-04-20
"cron" / "anacron" are for jobs that repeat.  It's a little more work to set up a cron job than it is to schedule a job with "at".  Cron provides mechanisms for specifying complicated repeating patterns for jobs. 

"at" is for jobs that should just occur one time.   It's handy for reminding you to do stuff.  You don't have to edit any files to schedule a job with "at", you just use the command line.

For example, here is one of the things I commonly use at for:  I'm sitting down to play an engrossing game of "Dwarf Fortress", but I have somewhere to be at 8:00.  So, I use "at" to shut off my music and verbally say the time aloud at 7:45 to remind me to leave.  Then I don't have to watch the time.

```

fhanson@fhanson:~$ at 7:45 pm
warning: commands will be executed using /bin/sh
at> quodlibet --pause
at> saytime
at> <EOT>
job 5 at Fri Apr 20 19:45:00 2007
fhanson@fhanson:~$ 

```

(Note that I hit Ctrl-d to exit the "at" prompt after I was done entering the 2 commands I wanted it to execute.  This is at the point in the output where it says <EOT>.)

It is amazing how handy and indispensable "at" becomes once you get used to it.

---

### Post by El_Matthews on 2007-04-23
thanks, I have become a little bit wiser ;)

---

