---
title: "/var/log/messages: Filled with -- MARK --"
date: 2006-10-21
forum: General Help
---

### Post by MikeBenza on 2006-10-21
I took a look at /var/log/messages today, and saw it's FILLED with this junk:

```
[size=1]Oct 12 12:04:47 localhost -- MARK --
Oct 12 12:24:48 localhost -- MARK --
Oct 12 12:44:48 localhost -- MARK --
Oct 12 13:04:48 localhost -- MARK --
Oct 12 13:24:48 localhost -- MARK --
Oct 12 13:44:49 localhost -- MARK --
Oct 12 14:04:49 localhost -- MARK --
Oct 12 14:24:49 localhost -- MARK --
Oct 12 14:44:49 localhost -- MARK --
Oct 12 15:04:50 localhost -- MARK --
Oct 12 15:24:50 localhost -- MARK --
Oct 12 15:44:50 localhost -- MARK --
Oct 12 16:04:50 localhost -- MARK --
Oct 12 16:24:51 localhost -- MARK --
Oct 12 16:44:51 localhost -- MARK --
Oct 12 17:04:51 localhost -- MARK --
Oct 12 17:24:51 localhost -- MARK --
Oct 12 17:44:51 localhost -- MARK --
Oct 12 18:04:52 localhost -- MARK --
Oct 12 18:24:52 localhost -- MARK --
Oct 12 18:44:52 localhost -- MARK --
Oct 12 19:04:52 localhost -- MARK --
Oct 12 19:24:53 localhost -- MARK --
Oct 12 19:44:53 localhost -- MARK --
Oct 12 20:04:53 localhost -- MARK --
Oct 12 20:24:53 localhost -- MARK --
Oct 12 20:44:54 localhost -- MARK --
Oct 12 21:04:54 localhost -- MARK --
Oct 12 21:24:54 localhost -- MARK --
Oct 12 21:44:54 localhost -- MARK --
Oct 12 22:04:55 localhost -- MARK --
Oct 12 22:24:55 localhost -- MARK --
Oct 12 22:44:55 localhost -- MARK --
Oct 12 23:04:55 localhost -- MARK --
Oct 12 23:24:55 localhost -- MARK --
Oct 12 23:44:56 localhost -- MARK --
Oct 13 00:04:56 localhost -- MARK --
Oct 13 00:24:56 localhost -- MARK --
Oct 13 00:44:56 localhost -- MARK --
Oct 13 01:04:57 localhost -- MARK --
Oct 13 01:24:57 localhost -- MARK --
Oct 13 01:44:57 localhost -- MARK --
Oct 13 02:04:57 localhost -- MARK --
Oct 13 02:24:58 localhost -- MARK --
Oct 13 02:44:58 localhost -- MARK --
Oct 13 03:04:58 localhost -- MARK --
Oct 13 03:24:58 localhost -- MARK --
Oct 13 03:44:59 localhost -- MARK --
Oct 13 04:04:59 localhost -- MARK --
Oct 13 04:24:59 localhost -- MARK --
Oct 13 04:44:59 localhost -- MARK --
Oct 13 05:04:59 localhost -- MARK --
Oct 13 05:25:00 localhost -- MARK --
Oct 13 05:45:00 localhost -- MARK --
Oct 13 06:05:00 localhost -- MARK --
Oct 13 06:25:00 localhost -- MARK --
Oct 13 06:45:01 localhost -- MARK --
Oct 13 07:05:01 localhost -- MARK --
Oct 13 07:25:01 localhost -- MARK --
Oct 13 07:35:37 localhost exiting on signal 15
Oct 13 07:35:38 localhost syslogd 1.4.1#17ubuntu7: restart.
....
[/size]
```

(Yes, I know it's an old one, but that's just the first one in the current log)

It repeats like that over and over.  It repeats on about 20 minute intervals (20 minutes and a third of a second, you could say).  So, I went back to see if there was an event 20 minutes and up to a second more before.  There was: a reboot:

```
[size=1]Oct 12 11:42:35 localhost shutdown[5036]: shutting down for system reboot
Oct 12 11:42:36 localhost kernel: [17180807.016000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 12 11:42:36 localhost kernel: [17180807.016000] apm: disabled on user request.
Oct 12 11:42:43 localhost kernel: [17180813.640000] nfsd: last server has exited
Oct 12 11:42:43 localhost kernel: [17180813.640000] nfsd: unexporting all filesystems
Oct 12 11:42:43 localhost kernel: Kernel logging (proc) stopped.
Oct 12 11:42:43 localhost kernel: Kernel log daemon terminating.
Oct 12 11:42:43 localhost exiting on signal 15
Oct 12 11:44:47 localhost syslogd 1.4.1#17ubuntu7: restart.[/size]
```

What could this possibly be?  Should I post up my whole messages file?

---

### Post by MKR. on 2006-10-21
That's your computer telling you "hi, I was working at so-and-so time". That log may be what allows you to narrow down the cause of a problem if one arises. :P

---

