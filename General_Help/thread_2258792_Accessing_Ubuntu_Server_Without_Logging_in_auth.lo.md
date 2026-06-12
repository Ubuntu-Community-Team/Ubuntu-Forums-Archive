---
title: "Accessing Ubuntu Server Without Logging in auth.log or syslog ?"
date: 2014-12-30
forum: General Help
---

### Post by chiques on 2014-12-30
Is it possible for a user to access an Ubuntu server without triggering a log entry of their information in /var/log/auth.log or /var/log/syslog ?

---

### Post by nerdtron on 2014-12-30
Just for a single user only?

If I'm not mistaken you can disable logging globally but not for a single user only.

---

### Post by chiques on 2014-12-31
So it in a security sense, monitoring the syslog and auth.log would give some indication if there is someone/something trying to access the system?

---

### Post by nerdtron on 2014-12-31
Yup. even passwordless ssh logins, even cron jobs (I think) are log on those files.

---

### Post by chiques on 2014-12-31
> **nerdtron said:**
> Yup. even passwordless ssh logins, even cron jobs (I think) are log on those files.

Thanks!

---

### Post by JKyleOKC on 2014-12-31
> **nerdtron said:**
> Yup. even passwordless ssh logins, even cron jobs (I think) are log on those files.Cron jobs are definitely logged. In fact the cron.hourly entries form the majority of my auth.log data.

---

### Post by Doug S on 2014-12-31
> **chiques said:**
> Is it possible for a user to access an Ubuntu server without triggering a log entry of their information in /var/log/auth.log or /var/log/syslog ?Hi Everyone,
Yes, I believe it is possible, and it has been on my "to do" list for a couple of years to investigate, but I just haven't got to it yet.
Use secure copy (scp) from somewhere else. Observe no entries whatsoever in any log in the /var/log directory.

---

### Post by chiques on 2014-12-31
> **Doug S said:**
> Hi Everyone,
Yes, I believe it is possible, and it has been on my "to do" list for a couple of years to investigate, but I just haven't got to it yet.
Use secure copy (scp) from somewhere else. Observe no entries whatsoever in any log in the /var/log directory.

I'll set this up and watch the logs. It will be interesting.

---

### Post by Doug S on 2014-12-31
Hi again,

I made a mistake. scp logins do show up in auth.log. Sorry.

---

