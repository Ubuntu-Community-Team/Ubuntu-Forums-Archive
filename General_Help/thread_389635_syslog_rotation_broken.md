---
title: "syslog rotation broken"
date: 2007-03-20
forum: General Help
---

### Post by jboehm on 2007-03-20
Hi,

So I noticed today that the last time syslog has been rotated was 12/24/06.  It has grown to 119MB.  How do I fix this?

Thanks,
Jon

---

### Post by jboehm on 2007-03-21
hmm .. it appears that /etc/cron.daily/sysklogd is not running.  I can run it manually but it appear to not work with the other daily tasks.

Where does cron.daily get logged to?  Is there a time out?  How would I find which task is killing cron.daily.

thanks,
Jon

---

