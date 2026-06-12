---
title: "How can I make Ubuntu really check for updates every day?"
date: 2017-01-31
forum: General Help
---

### Post by unflavored on 2017-01-31
I'm using Xenial. The computer is usually suspended, but it gets turned on every day. It is rarely rebooted. It doesn't check for updates every day, even though it's supposed to. Today I got the update for USN-3175-1, four days late. What can I do to make it check every day?

---

### Post by slitpdm on 2017-01-31
I would try cron-apt: [http://inguza.com/software/cron-apt](http://inguza.com/software/cron-apt)

---

### Post by geeksmith on 2017-01-31
If cron isn't set to check while the computer is awake then the job is skipped. You'll need to adjust any cron job to run while the computer is expected to be running. You could also use a script to check for updates when your computer awakes using the method described here: [https://wiki.debian.org/Hibernation](https://wiki.debian.org/Hibernation)

---

### Post by ian-weisser on 2017-01-31
In 16.04 and later, apt (including Unattended Upgrades) runs at a *random time* each day. The random time is chosen by systemd.

If the system is unavailable at that random time, then systemd will run apt (including u-u) a few minutes after the system becomes available again.

To check the last time an apt service has run, try:

```
$ ls -l /var/lib/apt/periodic/total 0
-rw-r--r-- 1 root root 0 Jan 31 10:19 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Jan 31 10:19 update-stamp
-rw-r--r-- 1 root root 0 Jan 31 10:19 update-success-stamp
-rw-r--r-- 1 root root 0 Jan 31 10:19 upgrade-stamp
```

To check the last and next times apt is scheduled to run, try:

```
$ systemctl list-timers apt-daily.timer
NEXT                         LEFT    LAST                         PASSED      UNIT            ACTIVATES
Tue 2017-01-31 20:59:18 CST  6h left Tue 2017-01-31 10:19:01 CST  4h 5min ago apt-daily.timer apt-daily.service


1 timers listed.
```

---

