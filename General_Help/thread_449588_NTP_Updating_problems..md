---
title: "NTP Updating problems."
date: 2007-05-20
forum: General Help
---

### Post by Smokeymcpawt on 2007-05-20
When trying to update my system clock, I check my daemon.log and see the following entries:
```
May 20 13:05:56 jareds ntpd_initres[4825]: ntpd returns a permission denied error!
May 20 13:06:56 jareds ntpd_initres[4825]: ntpd returns a permission denied error!

```

What exactly does this mean?

I'm using Ubuntu 7.04, with gnome.

---

### Post by bristleburger on 2007-05-20
Not sure, but maybe you can't update the system clock when ntpd is running.

A quick way to set your system clock is to execute this:
[INDENT]sudo ntpdate ntp.ubuntu.com[/INDENT]

But if you get a message that looks like this...
[INDENT]20 May 18:55:36 ntpdate[10641]: the NTP socket is in use, exiting
[/INDENT]
...then ntpd is running.

You can stop ntpd by executing:
[INDENT]sudo /etc/init.d/ntp stop[/INDENT]
Then set the system clock:
[INDENT]sudo ntpdate ntp.ubuntu.com[/INDENT]
And then start ntpd up again:
[INDENT]sudo /etc/init.d/ntp start[/INDENT]

---

