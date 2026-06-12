---
title: "TRIM - Am I Fully Covered?"
date: 2018-02-07
forum: General Help
---

### Post by Quarkrad on 2018-02-07
Recently installed** / **and **/home **on ssd.  I have the following terminal output:

```
dad@dadubuntu:~$ sudo hdparm -I /dev/sdd | grep "TRIM supported"
	   *	Data Set Management TRIM supported (limit 8 blocks)
dad@dadubuntu:~$ cat /etc/cron.weekly/fstrim
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all || true
```

I have read something like ......I also made a cron job for /home......  So, I'm a little worried - does the above cron job enable trim for **/ **and **/home** on my single ssd?

---

### Post by Quarkrad on 2018-02-07
Sorry - meant to post this in General

---

### Post by QIII on 2018-02-08
Moved to General Help

---

