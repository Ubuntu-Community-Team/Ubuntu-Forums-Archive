---
title: "ntp server?"
date: 2020-06-14
forum: General Help
---

### Post by hmiersch on 2020-06-14
ok, so i can turn on ntp servers in the settings app to synchronize the time with some NTP server out on the internet. so far so good. but how does ubuntu know which NTP server to use? where is that information stored?

---

### Post by Bashing-om on 2020-06-14
hmiersch; Hello

See the output of:
```

 systemctl status systemd-timesyncd.service

``` where we are pointed to the man page:
man:systemd-timesyncd.service(8)

[INDENT][INDENT]reading is good
[/INDENT][/INDENT]

---

### Post by TheFu on 2020-06-14
There are multiple different time sync methods on Linux.  ntp is the old method an usually accurate enough.  chrony is newer and sub-second accurate, so not as good as ntp msec accuracy.  There's an extreme ptp method which is usec accurate. I&#8217;ve never needed that.

I&#8217;m most familiar with ntp.  it is controlled by the /etc/ntp.conf for both the client and server.  Clients point to your server. Your server points to the internet ntp servers you want.  There's a great ntp.conf manpage for the settings.

---

