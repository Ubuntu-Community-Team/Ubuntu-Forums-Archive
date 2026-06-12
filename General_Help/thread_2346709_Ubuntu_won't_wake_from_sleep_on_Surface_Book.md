---
title: "Ubuntu won't wake from sleep on Surface Book"
date: 2016-12-17
forum: General Help
---

### Post by geluso on 2016-12-17
My computer never wakes up after it's suspended. I have no idea what's wrong. Here's some system information and system logs I've gathered:

uname -a
Linux geluso-surface 4.4.6-3-surface #tigerite ZEN SMP Tue May 24 13:22:59 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Dec 17 12:04:29 geluso-surface systemd[1]: Reached target Sleep.
Dec 17 12:04:29 geluso-surface systemd[1]: Starting Suspend...
Dec 17 12:04:29 geluso-surface systemd-sleep[5661]: Failed to connect to non-global ctrl_ifname: (nil)  error: No such file or directory
Dec 17 12:04:29 geluso-surface systemd-sleep[5663]: /lib/systemd/system-sleep/wpasupplicant failed with error code 255.
Dec 17 12:04:29 geluso-surface systemd-sleep[5661]: Suspending system...
Dec 17 12:06:21 geluso-surface rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="872" x-info="http://www.rsyslog.com"] start

I see some errors occurring there. There's two minutes between when the system is suspended and when it starts again. The computer just has a black screen. I press keys and push the power button and nothing happens. I have to hold the power button down for 10 seconds to initiate a hard shut down and reboot the computer before it works again.

Any idea what's going on here? Any help is appreciated. Thank you!

---

