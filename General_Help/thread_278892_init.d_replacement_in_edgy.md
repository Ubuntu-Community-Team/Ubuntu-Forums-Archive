---
title: "init.d replacement in edgy?"
date: 2006-10-17
forum: General Help
---

### Post by D!mon on 2006-10-17
There is a lot speaking about init.d replacement in edgy.
I've upgraded from dapper and hadn't enough time to play with it much yet, but it looks like my system still uses init.d, though while upgrading there were some messages about new init system.
How can I check if my system is using init.d replacement or how to turn it on?

Thanks,
Dmitry

---

### Post by Kateikyoushi on 2006-10-17
Edgy is using the new init called upstart, you do not have to turn it on, but the scripts aren't ready yet.


> What is the implementation plan?

Because this is process #1 we are changing, we want to make sure that we get it right. Therefore instead of releasing a fully-featured daemon and configuration to the world, we&#8217;re developing it in the following stages:
Principal development; at the end of this stage the daemon has been implemented and can manage jobs as described.
Replacement of /sbin/init while running the existing sysv-rc scripts. This is the shake-down test of the daemon, can it perform the same job as the existing sysvinit daemon without any regressions?
/etc/rcS.d scripts replaced by upstart jobs. These consitute the majority of tasks for booting the system into at least single-user mode, and contain many of the current ordering problems and race conditions. If the daemon solves the problems here, it will be a success.
Other daemon&#8217;s scripts replaced by upstart jobs on a package-by-package basis; this will be an ongoing effort during which upstart will continue running the existing sysv-rc scripts as well as its own jobs. During this time the event system may be tweaked to ensure it truly solves the problems we need.
Replcement of cron, atd, anacron and inetd. This will happen alongside the above and result in a single place to configure system jobs.
Modification of other daemons and processes to send events to init instead of trying to run things themselves.

The current plan is that we will be at least part of the way into stage #3 by the time edgy is released, with that release shipping with upstart as the init daemon and the most critical rcS scripts being run by it to correct the major problems

For edgy+1 we hope to have completed stage #5 and be at least part of the way into the implementation of stage #6. From the start of development of edgy+2, no new packages will be accepted unless they provide upstart jobs instead of init scripts and init scripts will be considered deprecated.

[Link]("http://www.netsplit.com/blog/articles/2006/08/26/upstart-in-universe")

---

### Post by D!mon on 2006-10-17
OK, I c. But release date is quite soom, as I understand, so init scripts will be replaced with upstart scripts soon automatically or   if not another question: can I switch to upstart right now manually to decrease boot time on my computer?

---

### Post by Kateikyoushi on 2006-10-17
You are using upstart right now, I assume the scripts will come with an update when they are finished.

Check the improvements of boots speed in [this thread]("http://ubuntuforums.org/showthread.php?t=241604&highlight=bootchart").

---

