---
title: "Failing to back up Evolution from cron job"
date: 2014-08-31
forum: General Help
---

### Post by Adam_Jacobs on 2014-08-31
I have recently upgraded from Ubuntu 12.04 to Ubuntu 14.04.

This seems to have messed up a cron job I had set up to backup my Evolution emails. I use the evolution-backup command line utility. This worked before, but doesn't work now. In fact it does work now if I run it manually from a terminal, but not if I run it from a cron job. The error message I get in the log file is as follows:

error: XDG_RUNTIME_DIR not set in the environment.
Cannot open display: 

Any idea why I'm getting that error and how I can fix it?

Many thanks
Adam

---

### Post by ian-weisser on 2014-08-31
> **Adam_Jacobs said:**
> The error message I get in the log file is as follows:

error: XDG_RUNTIME_DIR not set in the environment.
Cannot open display: 

Where did you get evolution-backup from? I don't seem to have it, and cannot locate a package providing command-line evo backup in the Ubuntu repositories.

The error message means that evolution-backup may look like a command line application, but it seems to require a display. Cron does not have a display to pass to e-b, so e-b stops. Cron is headless - it *never* has a display unless you explicitly assign one in the crontab or script.


Here's the dull detail:
XDG_RUNTIME_DIR is an *environment variable*. When you login and X starts, lots of environment variables tell applications about the desktop, environment, etc. You can see the list of current variables when you try the 'printenv' command.

Specifically, XDG_RUNTIME_DIR points to the /run/user/$USER_ID directory, where many of the applications you use keep some temporary data...including X storing session display data.

---

### Post by Adam_Jacobs on 2014-09-07
evolution-backup just came with Evolution. It's at /usr/lib/evolution/3.10/evolution-backup

This all worked on Ubuntu 12.04, but perhaps it's no longer the approved way of backing up Evolution under Ubuntu 14.04? Is there a better way to do things?

---

### Post by Adam_Jacobs on 2014-09-13
Bump?

---

### Post by ian-weisser on 2014-09-13
Ah, it's provided by libevolution.
Since I have never used it, I cannot answer why evolution-backup now requires a display.
I backup my mail a different way that seems not-relevant to your issue.

---

### Post by gordintoronto on 2014-09-14
I am using Evolution 3.2.3. Under File there is an entry, "Backup Evolution Data." I suspect the command-line approach has been deprecated.

---

### Post by Adam_Jacobs on 2014-09-16
Hm. So if command line backup is deprecated, what is now the approved way to back up Evolution mails? I'm quite happy to do it by any other method that works, but would like to be able to do it by some method that can be run as a cron job.

---

### Post by ian-weisser on 2014-09-16
> **gordintoronto said:**
>  I suspect the command-line approach has been deprecated.

True indeed, but I wonder if it's a bug instead?
Requiring a display seems an unusual way of disabling the feature to me.
Were I deprecating it, I would have removed it instead of merely breaking it.

I think Adam-Jacobs should file a bug report on the issue. 'evolution backup requires XDG_RUNTIME_DIR; cannot run from cron job'

When I try the command (logged in, using a display, it *seems* to work...though I've no idea if it really works).

I see two workarounds to continue using evolution-backup.

1) In your crontab, you can export the XDG_RUNTIME_DIR (and whatever else evolution-backup needs)
2) Or you can forget the cron route and run evolution-backup as a login/logout or other triggered script.

---

### Post by gordintoronto on 2014-09-16
An alternative would be to give in and run it from the Evolution menu. I have thousands of messages in about 30 folders, and the backup just takes a couple of minutes for me, on my five-year-old computer. You could have a cron job to remind you to do the backup...

---

