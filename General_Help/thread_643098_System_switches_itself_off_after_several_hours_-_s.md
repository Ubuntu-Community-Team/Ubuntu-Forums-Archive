---
title: "System switches itself off after several hours - says 'exiting on signal 15' in log"
date: 2007-12-17
forum: General Help
---

### Post by jnoreiko on 2007-12-17
I've set up a new system and it keeps switching itself off after about 10 hours. This is a really major problem as it's supposed to be streaming radio and storing an archive of output too.

This is what /var/log/syslog  says at that time:

```
Dec 17 14:38:54 seaside-logger init: tty4 main process (4475) killed by TERM signal
Dec 17 14:38:54 seaside-logger init: tty5 main process (4476) killed by TERM signal
Dec 17 14:38:54 seaside-logger init: tty2 main process (4479) killed by TERM signal
Dec 17 14:38:54 seaside-logger init: tty3 main process (4480) killed by TERM signal
Dec 17 14:38:54 seaside-logger init: tty1 main process (4481) killed by TERM signal
Dec 17 14:38:54 seaside-logger init: tty6 main process (4482) killed by TERM signal
Dec 17 14:38:55 seaside-logger avahi-daemon[5181]: Got SIGTERM, quitting.
Dec 17 14:38:55 seaside-logger avahi-daemon[5181]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.86.
Dec 17 14:38:59 seaside-logger exiting on signal 15
```

I googled for the signal 15 part, and an old bug to do with power management came up -- system rebooting because the kernel thinks the CPU is overheating.

So I tried booting with the option acpi=off.
This time it stayed up for longer -- nearly 48 hours. But it still turned itself off again.

Help! I've got to get this up and working for the holiday break :(

---

