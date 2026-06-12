---
title: "Cron does not work"
date: 2007-04-04
forum: General Help
---

### Post by ebike on 2007-04-04
Hi All,

I am having a problem with my hardware clock on my Mythtv box. It gains 20 secs evey hour, changing the battery doesn't help.

So as a temporary fix I thought I'd run a script in /etc/cron.houly/ that updates the time from
ntp, the script is:

> #!/bin/sh
/usr/sbin/ntpdate  nz.pool.ntp.org  2>&1 > /dev/null &


This script runs fine from the command line as a root user, but will not run every hour from cron.
Cron also does not run my other scripts that I put in the /etc/cron.daily/ directory.

The cron process is running.

>  ps -A |grep cron
 6967 ?        00:00:00 cron

Anyone got any idea's ?

---

### Post by ebike on 2007-04-07
Well I got my clock fixed at least. I had to add the "noapic" option to my kernel option line in /boot/grub/menu.1st. SO my clock is no longer running fast and I can use ntp-simple to keep it on ntp time.

Still don't know why cron will not work though ?:(

---

### Post by ebike on 2007-04-18
Bump anyone?

---

### Post by fanatik on 2007-04-19
please post the crontab entry, ie crontab -l, so we can see how you have scheduled it....

---

### Post by ebike on 2007-04-22
Hi,

Crontab -l returns nothing, for user "root" or my normal user. As mentioned in my previous post, I have
put the script I want to run in /etc/cron.daily so shoudn't the cron utility just pick that up? I havn't made any entries using crontab -e for any user ......

Thanks

---

### Post by hammanrj on 2007-04-23
I am having the same problem with ubuntu server edition, just upgraded from edgy.

*bump*

---

