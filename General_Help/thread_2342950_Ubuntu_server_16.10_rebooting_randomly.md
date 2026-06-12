---
title: "Ubuntu server 16.10 rebooting randomly"
date: 2016-11-11
forum: General Help
---

### Post by akgwin on 2016-11-11
Hi there, my new ubuntu server install appears to be rebooting randomly. I think this may be to do with the mdadm raid 5 array I just created as when that nears completion the server reboots. I don't think this is a hardware failure because of the way that the reboot times are structured, the on time gets smaller each time.
```

alex     pts/0        192.168.1.52     Fri Nov 11 12:10   still logged in
alex     tty1                          Fri Nov 11 10:34   still logged in
reboot   system boot  4.8.0-27-generic Fri Nov 11 10:34   still running
alex     tty1                          Fri Nov 11 10:33 - down   (00:00)
alex     tty1                          Fri Nov 11 10:05 - 10:29  (00:24)
reboot   system boot  4.8.0-27-generic Fri Nov 11 09:49 - 10:33  (00:43)
reboot   system boot  4.8.0-27-generic Fri Nov 11 09:23 - 10:33  (01:10)
reboot   system boot  4.8.0-27-generic Fri Nov 11 08:20 - 10:33  (02:13)
reboot   system boot  4.8.0-27-generic Fri Nov 11 07:53 - 10:33  (02:40)
reboot   system boot  4.8.0-27-generic Fri Nov 11 07:22 - 10:33  (03:10)
reboot   system boot  4.8.0-27-generic Fri Nov 11 06:57 - 10:33  (03:36)
reboot   system boot  4.8.0-27-generic Fri Nov 11 06:32 - 10:33  (04:01)
reboot   system boot  4.8.0-27-generic Fri Nov 11 06:08 - 10:33  (04:24)
reboot   system boot  4.8.0-27-generic Fri Nov 11 05:09 - 10:33  (05:24)
reboot   system boot  4.8.0-27-generic Fri Nov 11 04:20 - 10:33  (06:12)
reboot   system boot  4.8.0-27-generic Fri Nov 11 03:46 - 10:33  (06:47)
reboot   system boot  4.8.0-27-generic Fri Nov 11 03:12 - 10:33  (07:21)
reboot   system boot  4.8.0-27-generic Fri Nov 11 02:51 - 10:33  (07:42)
reboot   system boot  4.8.0-27-generic Fri Nov 11 02:19 - 10:33  (08:14)
reboot   system boot  4.8.0-27-generic Fri Nov 11 01:49 - 10:33  (08:43)

```

That's the result of running last for last night alone. The last result is from me rebooting intentionally this morning. I can't find anything is syslog that would suggest a crash, and the temperatures also seem fine so likely not an overheating problem. Anyone have any idea what this might be?

EDIT: I should also clarify that the machine powers down during reboot. It goes to bios screen and all.

EDIT2: Just rebooted again except this time the last output looks like this:
```
alex     pts/0        192.168.1.52     Fri Nov 11 13:12   still logged in
alex     tty1                          Fri Nov 11 12:45   still logged in
reboot   system boot  4.8.0-27-generic Fri Nov 11 12:44   still running
alex     pts/0        192.168.1.52     Fri Nov 11 12:10 - crash  (00:34)
alex     tty1                          Fri Nov 11 10:34 - crash  (02:10)
reboot   system boot  4.8.0-27-generic Fri Nov 11 10:34   still running
alex     tty1                          Fri Nov 11 10:33 - down   (00:00)
alex     tty1                          Fri Nov 11 10:05 - 10:29  (00:24)

```

---

