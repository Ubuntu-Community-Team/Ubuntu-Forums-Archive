---
title: "pre and postrotate for system logs"
date: 2008-02-09
forum: General Help
---

### Post by konsole on 2008-02-09
What is the recommended Ubuntu method to run pre and postrotate commands on system log rotations? syslog, messages etc.

Ubuntu doesn't use logrotate to rotate system logs and syslogd-listfiles doesn't know anything about prerotate and postrotate commands.

---

### Post by dcstar on 2008-02-10
> **konsole said:**
> What is the recommended Ubuntu method to run pre and postrotate commands on system log rotations? syslog, messages etc.

**Ubuntu doesn't use logrotate to rotate system logs** and syslogd-listfiles doesn't know anything about prerotate and postrotate commands.

It doesn't?, funny, on my system **logrotate** seems to work fine.

---

### Post by konsole on 2008-02-10
> **dcstar said:**
> It doesn't?, funny, on my system **logrotate** seems to work fine.

Care to post your logrotate files that rotate the system logs?

---

### Post by andrew.46 on 2008-02-11
Hi,

Seems a little odd:

> **konsole said:**
> Care to post your logrotate files that rotate the system logs?

Have you had a look at /etc/logrotate.conf?

                Andrew

---

### Post by konsole on 2008-02-12
> **andrew.46 said:**
> Hi,
Seems a little odd:
Have you had a look at /etc/logrotate.conf?
                Andrew

Thanks for your reply, but > Care to post your logrotate files that rotate the system logs? was a challenge to an ill-informed poster dcstar as I knew that he would be unable to post the files.

You see, if anyone had taken the trouble to properly read my question, they would have seen that I am clearly referring to system logs. Refer to /etc/syslog.conf if in doubt.

Logrotate is functioning fine on my system and rotates all non-system logs without a problem. It is /usr/sbin/syslogd-listfiles, /etc/cron.daily/sysklogd and /usr/bin/savelog that rotates system logs.

So I'll repeat my question: **What is the recommended Ubuntu method to run pre and postrotate commands on system log rotations? syslog, messages etc.**

---

