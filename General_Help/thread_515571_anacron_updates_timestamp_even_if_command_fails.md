---
title: "anacron updates timestamp even if command fails"
date: 2007-08-02
forum: General Help
---

### Post by Saverio on 2007-08-02
Hi!

I set some scheduled commands (to backup my system) in anacron.
They run as required, at the scheduled time or whenever the computer turns on.

The problem is that the script sometimes return an error (exit code 1) because the external hard disk is not mounted. This is perfectly ok, but I would like that anacron DOES NOT update the timestamp in this case! I think this should be its correct behavior.
If the timestamp is not updated, anacron would try to backup my system again the next time anacron is invoked and hopefully it would find the external hard drive.

Is there any workaround you know? I tried creating a backup script that removes the timestamp if it fails to backup, but unfortunately anacron updates the timestamp when the command exits.

Another thing: when is anacron invoked, a part from the boot? I found for example that its called when the AC adapter is plugged in... any other time?
Thanks a lot
Saverio

---

### Post by mannheim on 2007-08-02
In addition to boot time, anacron gets run once a day because cron launches anacron: the file that controls this is the file /etc/cron.d/anacron. (Probably you already figured this out.)

One problem with having anacron behave as you suggest is that it would break other existing usages. For example, an anacron job often has something like

```
test ...something... && /usr/bin/somescript --some_arguments
```

to run a script if a test condition holds. If the test fails, this line will return 1.

A different approach to your problem (one of many) is to just get your backup script to create a timestamp somewhere each time it does a successful backup. Then put a test at the beginning of the backup script to read the timestamp of the last backup and continue with a new backup only if that timestamp is sufficiently far in the past (eg one week, for weekly backups). Then get cron or anacron to call your backup script every hour or every day, or whatever. In other words, make the backup script responsible for decisions involving timestamps and the like.

---

### Post by Saverio on 2007-08-02
> **mannheim said:**
> In addition to boot time, anacron gets run once a day because cron launches anacron: the file that controls this is the file /etc/cron.d/anacron. (Probably you already figured this out.)

Yes, I've seen it. Most of the time is the one at boot that actually does something for me, and this is the problem: sometimes I turn on my computer but I don't login for some minutes. Anacron executes the backup script, but the external hard disk is not mounted because automount is not active. :(

> **mannheim said:**
> One problem with having anacron behave as you suggest is that it would break other existing usages. For example, an anacron job often has something like

```
test ...something... && /usr/bin/somescript --some_arguments
```

to run a script if a test condition holds. If the test fails, this line will return 1.

You're right, I tought it could be a problem for other existing solutions, and you found a clear example.

> **mannheim said:**
> A different approach to your problem (one of many) is to just get your backup script to create a timestamp somewhere each time it does a successful backup. 
[CUT]
In other words, make the backup script responsible for decisions involving timestamps and the like.

In other words, write my own anacron :)
Other solutions? I was thinking about calling those anacron jobs (for example with another anacrontab file) every time the external USB disk is automounted. Do you have any idea of how I can execute a script when my hard disk is auto mounted? Even better, only that specific drive?

I thought about checking the option "Auto run programs on new drives and media" in Ubuntu preferences... does it ask for confirm every time?

Thanks a lot for your reply!
Saverio

---

### Post by mannheim on 2007-08-02
> **Saverio said:**
> 
In other words, write my own anacron :)


That's a fair comment; but this part isn't hard:

```
#! /bin/bash

# Run a backup script only if more than 12 hours has passed since
# completion of last backup: 

half_a_day=$(( 12 * 60 * 60 ))

timestamp_file=$HOME/backup-timestamp

if [ -e $timestamp_file ]; then
    time_of_backup=`stat --format=%Y $timestamp_file`
    time_now=`date "+%s"`
    if (( $time_of_backup >= $time_now - $half_a_day )); then
        exit 0;
    fi
fi

run_backup && touch $timestamp_file

```

---

### Post by Saverio on 2007-08-02
Thanks a lot for spending some time on it!

I think I'll use it, and I'll call the script from crontab, hourly or so.

Ciao!
Saverio

---

