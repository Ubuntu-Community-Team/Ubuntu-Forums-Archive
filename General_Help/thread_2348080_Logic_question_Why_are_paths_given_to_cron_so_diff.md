---
title: "Logic question: Why are paths given to cron so different?"
date: 2016-12-31
forum: General Help
---

### Post by f00dl3 on 2016-12-31
Why are the path environmental variables given to jobs that run from a cron task so different than environmental variables set up in /etc/sudoers or environmental variables given to root/sudo su?

To me it doesn't make any logical sense what so ever that cron tasks don't have the same environmental variables when they are set to run as root - for example, a cron task kicked off as root does not even have access to basic folders such as /usr/local/bin or /usr/bin. Not only is this annoying from a script writing perspective, but it's in general just confusing because if the script runs as root, shouldn't it have all the environment settings as root?

---

### Post by TheFu on 2016-12-31
Never trust the PATH.  Best practices for all scripting is to fully specify the exact program you want inside your scripts. That makes this a non-issue.  
cron is not interactive.
sudoers are interactive, usually.  Different PATHs for different purposes.  If you don't like it, change them. Just be prepared for any repercussions.

It is your system.

---

