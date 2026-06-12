---
title: "I'd like to renice beagled - need explanation of startup script"
date: 2007-01-26
forum: General Help
---

### Post by ranarion on 2007-01-26
I'm running Kerry Beagle on a Laptop and would like to control its behaviour more. 

I found beagled is started by a crontab entry (default should be /etc/cron.daily/beagle-crawl-system). In this script, after some preparations, the main indexing process is started by

```
 eval nice -n 19 $IONICE su -s /bin/bash $CRAWL_USER -c \"MONO_SHARED_DIR=$MONO_SHARED_DIR /usr/sbin/beagle-build-index --target /var/cache/beagle/indexes/$CRAWL_INDEX_NAME $OPTIONS $CRAWL_PATHS\" > /dev/null 2>&1

```

My anacrontab, stripped to the interesting section:

```
SHELL=/bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin

1       5       cron.daily       nice run-parts --report /etc/cron.daily
7       10      cron.weekly      nice run-parts --report /etc/cron.weekly
@monthly        15      cron.monthly nice run-parts --report /etc/cron.monthly

```

If I take a look at the running demon with top or a similar tool, however, it is not niced to 19, but has a niceness of 0. Why that?

Another question: Is there a way I can have the demon run only if I'm on AC power?

---

### Post by kidders on 2007-01-27
Hi there,

I've been keeping an eye on this thread because I'm interested in the right answers to your questions. Since nobody's replied for 11 hours now, I might as well try though!

I ***_think_*** the answers are something like this ... (sorry if I turn out to be wrong!) ...

> If I take a look at the running demon with top or a similar tool, however, it is not niced to 19, but has a niceness of 0. Why that?Strictly speaking, I'd say the command "su" is what's niced. Of course, you would *think* that processes spawned by another one would inherit their parents' niceness, but perhaps something is deliberately overriding it?

It looks as if the process chain goes su -> bash -> beagle. How niced are "su" and "bash"?

> Is there a way I can have the demon run only if I'm on AC power?This should be easy ... you just have to know where to look. Unfortunately, I can't check this (because I don't currently have Linux on my laptop), but I'll try to point you in the right direction...

How familiar are you with procfs and sysfs? These are filesystem interfaces to your kernel & hardware. For the mostpart, they contain pseudo-files that you either read from or write to, to get or set things about how your system works. Anyhow, if you have a look around in them, you should be able to find some power-related stuff. I'd be stunned if there weren't something in there that can tell you what power source you're currently using.

Sorry for being so vague. :-( If I were you, I'd make liberal use of "find" and see what I could turn up. Imagine, for the sake of argument, you find a file that has a "1" in it when you're on AC power. You would then be able to do something like:

```
if [ `cat /sys/devices/somewhere/something` -eq 1 ]; then
       # Only execute when on AC power
fi
```

**Edit:**

The power thing was annoying me, so I threw Linux onto my PowerBook, just to take a look. I think I've found what you need. :-)

Hopefully, you have a file called /proc/apm on your machine. It contains 9 fields:

[LIST=1]
[*]Driver version
[*]BIOS version
[*]APM flags
[*]A/C status
[*]Battery status
[*]Battery flags
[*]Battery %
[*]Battery time
[*]Time units
[/LIST]

Anyhow, field 4 is what you're after:

```
if [ -r /proc/apm ]; then
	if [ "`cat /proc/apm | cut -d" " -f 4`" = "0x01" ]; then
		# Execute only if on A/C power
	fi
else
	echo "Can't determine power source"
fi
```

Hope that helps.

---

### Post by ranarion on 2007-01-28
Many thanks for your answers! I had talked to one of Beagle's developers on their IRC channel two days ago, and wanted to sum up our talk for other forum readers now when I saw your post.

Unfortunately, we found out that the version of Beagle shipped with Breezy, namely 0.2.9, had a bug that got triggered when it tried to index certain kinds of .jar Files. As I have lots of jarfiles lying around everywhere, this caused the indexing demon to abort and re-index *all* of my files quite often, thus causing a lot of unneccessary system load. So I'll wait for the new Version of Beagle that should come out in the next few weeks before digging deeper into the issue.

Your hints on using /proc directly is, however, very helpful! I was looking in the wrong places...

---

