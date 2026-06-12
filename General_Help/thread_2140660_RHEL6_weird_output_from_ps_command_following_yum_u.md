---
title: "RHEL6: weird output from ps command following yum updates"
date: 2013-04-30
forum: General Help
---

### Post by SuaSwe on 2013-04-30
Hi all,

After a yum update on a RHEL6 system earlier (which included kernel upgrades) some weirdnesses are being seen in the ps output, as per below:

```

[user@server ~]$ ps -ef | grep http
root      3681     1 99 15:42 ?        213508-01:40:43 /usr/sbin/httpd
apache    3695  3681 99 15:42 ?        833-20:57:21 /usr/sbin/httpd
apache    3696  3681 99 15:42 ?        1667-17:54:42 /usr/sbin/httpd
apache    3697  3681 99 15:42 ?        1042-08:11:41 /usr/sbin/httpd
apache    3698  3681 99 15:42 ?        625-09:43:00 /usr/sbin/httpd
apache    3699  3681 99 15:42 ?        625-09:43:00 /usr/sbin/httpd
apache    3700  3681 99 15:42 ?        312-16:51:30 /usr/sbin/httpd
apache    3701  3681 99 15:42 ?        208-11:14:20 /usr/sbin/httpd
apache    3703  3681 99 15:42 ?        233-16:51:09 /usr/sbin/httpd
apache    3704  3681 99 15:42 ?        208-11:14:20 /usr/sbin/httpd
apache    3705  3681 99 15:42 ?        208-11:14:20 /usr/sbin/httpd
apache    3706  3681 99 15:42 ?        416-22:28:40 /usr/sbin/httpd
apache    3707  3681 99 15:42 ?        208-11:14:20 /usr/sbin/httpd
apache    3708  3681 99 15:42 ?        208-11:14:20 /usr/sbin/httpd
apache    3709  3681 99 15:42 ?        208-11:14:20 /usr/sbin/httpd
apache    3710  3681 99 15:42 ?        208-11:14:20 /usr/sbin/httpd
apache    3769  3681 99 15:42 ?        208-11:14:20 /usr/sbin/httpd
apache    3856  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3857  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3913  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3914  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3915  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3916  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3975  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3976  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3977  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3978  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3979  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3980  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3981  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    3982  3681  0 15:42 ?        00:00:00 /usr/sbin/httpd
apache    4476  3681  0 15:43 ?        00:00:00 /usr/sbin/httpd
502       4613  4583  0 15:43 pts/1    00:00:00 grep http

```

The lower half-ish of the output looks normal, but anove that a number and hyphen is being added to the timestamp, e.g. "213508-01:40:43".

Has anyone seen this before and knows what causes it?

Cheers!

SuaSwe

---

### Post by dino99 on 2013-04-30
you seems far from home :lolflag:
sadly cant help here ;)

---

### Post by SuaSwe on 2013-04-30
Well, I thought as it's an issue with a UNIX command and there is an option for [other_os], that it might be acceptable and that I might luck out with someone who might've coincidentally come across it recently - sorry. :D In my defence I usually use this forum for Linux only. ;)

---

