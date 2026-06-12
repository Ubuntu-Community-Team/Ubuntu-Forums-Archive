---
title: "Seemingly Random Hangs/Lockups"
date: 2008-05-10
forum: General Help
---

### Post by JamieC on 2008-05-10
I currently dual boot Windows Vista and Ubuntu 8.04 on a laptop. I had been running 7.10 since the release and experienced no problems. Instead of upgrading I decided to do a clean install to remove obsolete and residual files.

When using Hardy Heron I randomly experience hangs. I am unable to use the keyboard or mouse meaning I need to hard shutdown.

What log files can I check to determine the cause of the problem? I tried dumping the contents of various log files every second in hope that when I power the laptop back on after the hang the most recent log file would yield some information but I'm not really sure what I'm looking for.

Any help would be much appreciated, thanks in advance.

---

### Post by Mr. Picklesworth on 2008-05-10
Could you check your keyboard, to see if the caps lock or scroll lock lights are flashing? It could be a kernel panic...

This behaviour has been observed in a few cases, and is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996"). People seem uncertain whether it is an individual driver issue, an issue with functionality practically everyone uses (sata input/output stuff), or a version of the kernel with horribly broken error handling. It could really be any of those things, sadly.
The bug report has lots of comments that may help you resolve, or at least pinpoint, your particular issue.

One thing to look at: Is there any new information in your system log after restarting?
As for how to restart in this situation, you can use some key combinations involving SysRQ (usually doubles as Print Screen) in order to slightly more happily restart the computer and (hopefully) better examine the issue. Some direction on [this forum thread]("http://bbs.archlinux.org/viewtopic.php?pid=330528#p330528") and [this article]("http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=19672"). "Fun" shortcut: alt-sysrq-reisub.

There is a way to get the kernel to do dump information to the log, too... alt-sysrq-e, I believe?

---

