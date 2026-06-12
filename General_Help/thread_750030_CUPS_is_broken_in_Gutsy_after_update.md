---
title: "CUPS is broken in Gutsy after update?"
date: 2008-04-09
forum: General Help
---

### Post by dda on 2008-04-09
I was able to add and use printer in Gutsy, but recently when i tried to print, noticed that my job was held. After trying to fix it, I removed printer, and was not able to add a new both via web console and gnome program. In logs I found:

```
E [07/Apr/2008:22:02:21 +0000] [CGI] Unable to execute "/usr/lib/cups/backend/hal" - Permission denied
E [07/Apr/2008:22:02:21 +0000] [CGI] Unable to execute "/usr/lib/cups/backend/cups-pdf" - Permission denied
E [07/Apr/2008:22:02:21 +0000] [CGI] Unable to execute "/usr/lib/cups/backend/beh" - Permission denied
E [07/Apr/2008:22:02:21 +0000] [CGI] Unable to execute "/usr/lib/cups/backend/canon" - Permission denied
E [07/Apr/2008:22:02:21 +0000] [CGI] Unable to execute "/usr/lib/cups/backend/bluetooth" - Permission denied
E [07/Apr/2008:22:12:01 +0000] PID 2502 (/usr/lib/cups/cgi-bin/printers.cgi) stopped with status 22!
E [07/Apr/2008:22:12:04 +0000] PID 2506 (/usr/lib/cups/cgi-bin/admin.cgi) stopped with status 22!
E [07/Apr/2008:22:13:09 +0000] PID 2511 (/usr/lib/cups/cgi-bin/admin.cgi) stopped with status 22!

```
And then with DEBUG2 level:

```
d [08/Apr/2008:00:07:05 +0000] cupsdStartProcess("/usr/lib/cups/daemon/cups-driverd", 0x7fffdd2cb750, 0x7fffdd2cb390, -1, 10, 6)
D [08/Apr/2008:00:07:05 +0000] [CGI] /usr/lib/cups/daemon/cups-driverd started - PID = 6574
I [08/Apr/2008:00:07:05 +0000] Started "/usr/lib/cups/daemon/cups-driverd" (pid=6574)
D [08/Apr/2008:00:07:05 +0000] cupsdSendCommand: 7 file=8
d [08/Apr/2008:00:07:05 +0000] cupsdAddSelect: fd=8, read_cb=0x40f200, write_cb=(nil), data=0x6aac60
d [08/Apr/2008:00:07:05 +0000] process_children()
E [08/Apr/2008:00:07:05 +0000] PID 6574 (/usr/lib/cups/daemon/cups-driverd) stopped with status 22!
d [08/Apr/2008:00:07:05 +0000] cupsdDoSelect: polling 5 fds for 1 seconds...
d [08/Apr/2008:00:07:05 +0000] cupsdDoSelect: epoll() returned 2...
d [08/Apr/2008:00:07:05 +0000] cupsdDoSelect: Read on fd 5...
D [08/Apr/2008:00:07:05 +0000] [CGI] /usr/lib/cups/daemon/cups-driverd: Permission denied

```

I think I did not manually change anything. In dpkg.log I found:

```
2008-04-03 10:38:12 upgrade cupsys 1.3.2-1ubuntu7.5 1.3.2-1ubuntu7.6
2008-04-03 10:38:10 upgrade cupsys-common 1.3.2-1ubuntu7.5 1.3.2-1ubuntu7.6
```
.. and other cups-related packages.

I found several "status 22" posts in forums, but nothing applied to my case. By experiment I found that if I add "User dda" (this is my username) to /etc/cups/cupsd.conf, everything works. But I guess it won't work for other local users in the system.

So, what happened? I compared permissions of cupsd daemon, and the backends and CGIs - all were correct (root:root, 755). In an older system, Feisty with cups 1.2.8, some permissions are different, i.e. there is user cupsys, in my system there is no such user, I think that was changed in cups.

Any help is appreciated.

Regards,
Dmitry.

---

### Post by dda on 2008-04-22
No ideas?..

---

### Post by dda on 2008-04-25
I found it: it was a wong permissions issue. More details here: [http://www.linuxquestions.org/questions/linux-software-2/cups-is-broken-in-ubuntu-gutsy-after-update-637022/#post3133082](http://www.linuxquestions.org/questions/linux-software-2/cups-is-broken-in-ubuntu-gutsy-after-update-637022/#post3133082)

Regards,
Dmitry.

---

