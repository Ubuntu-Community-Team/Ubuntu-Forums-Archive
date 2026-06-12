---
title: "Ubuntu Edgy bug for cron??"
date: 2007-02-16
forum: General Help
---

### Post by Toet on 2007-02-16
I'm trying to backup my discs with a script to run every hour.

Reading on the internet about cron, it seems to be enough to put a executable script in the /etc/cron.hourly directory.

(the script is working when I run it from the prompt, path of the program in the script is in the /etc/crontab and also (to be sure) in the script itself)

So this is what I did, but the script is not run at all. Why not? Is this a bug in Ubuntu Edgy?

Am I making a mistake in my thinking or conclusions? :-k 

Anyone?

---

### Post by muralpennies on 2007-02-16
Cron does not run in the same environment as a normal user, so try specifying the full path to every command in your script.

Like:
/usr/bin/rsync

Not:
rsync

---

### Post by Toet on 2007-02-16
I did.

---

### Post by muralpennies on 2007-02-16
Okay, add the following at the end to your crontab entry:
```
> /tmp/crontab_output.txt 2>&1
```

This will redirect standard output (1) and standard error (2) to /tmp/crontab_output.txt.  You should see some output in that file, unless you're redirecting all output within your script.

The complete command would look something like the following:
```
1 2 * * * /usr/bin/local/myprog.sh > /tmp/crontab_output.txt 2>&1
```

---

### Post by Toet on 2007-02-17
Now we are at the essence of maybe my misunderstanding or a bug.

In my opinion there should be no entry in the crontab for my script cause I've put my script in the /etc/cron.hourly directory. Like all the standard scripts are in the /etc/cron.daily directory. All these standard scripts don't have a crontab entry either.

My crontab (I didn't change it ever):

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6	* * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6	1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

My anacrontab (didn't change it aswell):

# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

So is it my misconception of the concept or is there something wrong in the configuration of default ubuntu edgy regarding cron and anacron?

---

### Post by keithweddell on 2007-02-17
Here's something to check.  Does your script name have a "." (period) in it?  It seems to be little known but files called by cron cannot use "."  It causes much frustration when there seems to be no reason for the script failing.

Keith

---

### Post by Toet on 2007-02-17
Thanks a lot! Indeed my script was called .sh and I removed the .sh, and now for the first time my script is working. My scheduled backups are now running.

---

