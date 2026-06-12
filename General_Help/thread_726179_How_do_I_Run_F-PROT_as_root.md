---
title: "How do I Run F-PROT as root?"
date: 2008-03-16
forum: General Help
---

### Post by wayfarer51 on 2008-03-16
I have a script running in cron to run F-Prot Virus Scanner once a day.  My problem is, it needs to be root to test some of the files.  Since the script execution is automated, and frequently unattended at test time, I don't want to have to roll out of bed at 4 AM to "sudo in".[LIST=1]
[*]How could I do this?
[*]If I do it this way, am I leaving my box open for intrusion?
[*]Should I just accept that some files won't get checked?[/LIST]If someone could help me, I'd very much appreciate it.

Thanks,
Neill

---

### Post by cmnorton on 2008-03-16
As to the first part, you need to look at entries in /etc/cron, and set up something similar. root would be the user. You'd edit /etc/cron by using sudo vi, sudo emacs, or sudo your favorite editor and then entering your password, assuming your username was the one who set up Ubuntu.

If you prefer the method of logging in as root and using crontab -e, then you'd omit the field for user, because invididual crontabs do not need the user field. Personally, I don't like this latter approach. Instead I use the master /etc/crontab. For us it houses all the action that's going on as batch jobs. One of our vendors loves the crontab -e approach, so I've mirrored things that way on our primary and backup systems for consistency.

man -a crontab will give you the basics of cron and the table layout.

---

