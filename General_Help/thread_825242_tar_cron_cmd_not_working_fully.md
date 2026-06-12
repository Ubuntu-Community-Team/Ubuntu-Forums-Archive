---
title: "tar cron cmd not working fully"
date: 2008-06-10
forum: General Help
---

### Post by mowgliee on 2008-06-10
i have a tar cmd in an executable file in my cron.daily dir.  if i manually execute the file, it works as expected.

however each night (when cron daemon is supposed to run the file) cron runs the file, produces the 3 tar backups i want but they are just 16k in size.  they should be 200MB to 1GB each.

again it all works as expected when i manually execute the script file in cron.daily.  its only when cron attempts to run it automatically.

and its not the other script files in cron.daily dir cause i've run them all at once manually with no issues.

this is on feisty.  and its failed since install.  the same file works with cron on fedora.  what could be killing the tar creation?  and why does it do so for all 3 files?

and i dont have any error messages in the logs either!

---

### Post by mowgliee on 2009-05-31
update:

based on another thread on here, i decided to test some things in crontab:

if i leave crontab w/ shell=/bin/sh, tar fails midway.
if i change crontab to shell=/bin/bash, tar fails midway but at later point.
if i add "> /tmp/tarlogfile" at end of tar command, tar succeeds 100% and log file proves it!

but i dont want or need that log file; plus i want to know the true cause of this problem. otherwise i cant rely on other backups being thorough backups (i was just testing a small list of files to get the above symptoms; real backups will be a few gigs).

so anyone have any idea why it would work w/ redirecting output but not otherwise?

irony is i cant tell when/on what file the tar fails b/c it only fails if i dont redirect the output!  HELP!

---

### Post by mowgliee on 2010-10-17
bump bump

---

### Post by DaithiF on 2010-10-18
Hi,
the short answer is to put 
```
MAILTO=""
```
at the top of your crontab.

The reason is that cron expects to email you the output of the commands it runs.  However ubuntu desktop doesn't come with a mail transfer agent by default, and so cron opens a pipe to a (non-existing) mail program.  Once a certain amount of output has been buffered, an error occurs which takes down your cronjob part way through.

If the amount of output produced by your job is less than the size of the buffer your command would succeed.  But since you're tar'ing up files, and I would guess you're using the -v verbose flag (ie. printing each file being archived), then you're generating lots of output and so your process fails.  As you've seen redirecting output solves the problem since you then don't fill the buffer.

But the better way is to define the MAILTO as mentioned above, when you do this cron then doesn't attempt to pipe the output into a mail command.

This *may* have been fixed in 10.10 ... I'm waiting for my maverick upgrade to finish so I can confirm.

---

### Post by jonbonjovi on 2011-03-02
> **DaithiF said:**
> Hi,
the short answer is to put 
```
MAILTO=""
```
at the top of your crontab.

The reason is that cron expects to email you the output of the commands it runs.  However ubuntu desktop doesn't come with a mail transfer agent by default, and so cron opens a pipe to a (non-existing) mail program.  Once a certain amount of output has been buffered, an error occurs which takes down your cronjob part way through.

If the amount of output produced by your job is less than the size of the buffer your command would succeed.  But since you're tar'ing up files, and I would guess you're using the -v verbose flag (ie. printing each file being archived), then you're generating lots of output and so your process fails.  As you've seen redirecting output solves the problem since you then don't fill the buffer.

But the better way is to define the MAILTO as mentioned above, when you do this cron then doesn't attempt to pipe the output into a mail command.

This *may* have been fixed in 10.10 ... I'm waiting for my maverick upgrade to finish so I can confirm.

Man, you saved the day!

---

### Post by psusi on 2011-03-02
Better yet, install a mail server so you actually get the results.

---

