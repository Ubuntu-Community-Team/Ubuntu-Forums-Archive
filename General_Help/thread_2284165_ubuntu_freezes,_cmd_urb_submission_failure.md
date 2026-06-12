---
title: "ubuntu freezes, cmd urb submission failure"
date: 2015-06-27
forum: General Help
---

### Post by JeanCr on 2015-06-27
Hi,
Since 2 days my server running ubuntu 14 / kde has freezing so far 3 times now. I started to invest and fixed some thing with apt-get sources list that were wrong, after that i did a full update/upgrade, then i started investigating logs.
The logs for the two days since the problem are huge. it starts here:

```

Jun 26 03:48:59 server kernel: [41962.284561] usb 2-1: USB disconnect, device number 2
Jun 26 03:48:59 server kernel: [41962.296034] usb 2-1: URB BAD STATUS -108
Jun 26 03:49:00 server kernel: [41962.390781] sd 5:0:0:0: [sdc] Synchronizing SCSI cache
Jun 26 03:49:00 server kernel: [41962.390815] sd 5:0:0:0: cmd urb submission failure
Jun 26 03:49:00 server kernel: [41962.390825] sd 5:0:0:0: cmd urb submission failure
Jun 26 03:49:00 server kernel: [41962.390827] sd 5:0:0:0: cmd urb submission failure
Jun 26 03:49:00 server kernel: [41962.390829] sd 5:0:0:0: cmd urb submission failure

```

The last line is repeated some 200 times, after that the log contains numerous lines like this
```

Jun 26 03:49:00 server kernel: [41962.391734] sd 5:0:0:0: cmd urb submission failure
Jun 26 03:49:00 server kernel: [41962.391736] sd 5:0:0:0: cmd urb submission failure
Jun 26 03:49:00 server kernel: <
Jun 26 03:49:00 server kernel: 
Jun 26 03:49:00 server kernel: [41962.392918
Jun 26 03:49:00 server kernel: [41962.39
Jun 26 03:49:00 server kernel: [41962.3929
Jun 26 03:49:00 server kernel: [41962.392
Jun 26 03:49:00 server kernel: [41962.3929
Jun 26 03:49:00 server kernel: [41962.39
Jun 26 03:49:00 server kernel: [41962.3929
Jun 26 03:49:00 server kernel: [41962.392
Jun 26 03:49:00 server kernel: [41962.392
Jun 26 03:49:00 server kernel: [41962.39294
Jun 26 03:49:00 server kernel: [41962.392943
Jun 26 03:49:00 server kernel: [41962.3929

```

This repeats endlessly.

Is this some usb device failing? I've got 4 usb drives connected to it as a nas.

Ps. just noticed one of the powerplugs on one usb drive was a little loose...

---

### Post by dino99 on 2015-06-27
if you want to know about possible devices failure, you can load the partitioner, it should show a red triangle or the like if a problem exist.
then i wonder what 'urb' is; do you have an idea about it ?

---

### Post by JeanCr on 2015-06-27
Thx, Kde partition manager does not display any errors.
No idea what urb is. But i strongly suspect a power cord that was a bit loose on one of the drives. [knocks on wood]
ps, what's amazing is the size of /var/log/syslog
```

jean@server:~$ l /var/log/syslog*
-rw-r----- 1 syslog adm 3474514248 Jun 27 08:41 /var/log/syslog.1

```

---

