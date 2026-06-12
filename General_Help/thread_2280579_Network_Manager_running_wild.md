---
title: "Network Manager running wild"
date: 2015-05-31
forum: General Help
---

### Post by JKyleOKC on 2015-05-31
For several days now, I've been seeing more than 50 MB of /var/log/syslog being created every 12 hours!

The only clue to the problem that I've found is this:```
May 31 22:33:53 mehitabel NetworkManager[850]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 31 22:33:53 mehitabel NetworkManager[850]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May 31 22:33:53 mehitabel NetworkManager[850]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 31 22:33:54 mehitabel NetworkManager[850]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May 31 22:33:54 mehitabel NetworkManager[850]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May 31 22:34:13 mehitabel NetworkManager[850]: <info> (eth0): device state change: activated -> failed (reason 'ip-config-unavailable') [100 120 5]
May 31 22:34:13 mehitabel NetworkManager[850]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 31 22:34:16 mehitabel NetworkManager[850]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 31 22:34:16 mehitabel NetworkManager[850]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]

```

I retain syslog for a total of seven days after the current day, and all seven copies are filled with this sequence, round the clock. I simply selected one complete cycle of the reports, plus a few more to make it clear that the cycle was starting over.

I run named to provide a local DNS server, and each time that ip-config is launched, named is reloaded.

This continual reloading of DNS adds greatly to my WAN traffic, and causes noticeable delay in keyboard response. I'm looking for suggestions on how to bring Network Manager back under control. Restarting has had no effect.

The system is Xubuntu 14.04 with all current updates installed.

---

### Post by JKyleOKC on 2015-06-01
Finally found and fixed. Turned out that somehow the "IPV6 required" checkbox for eth0 had been checked, although I do not use IPV6 locally and it should have been clear. Perhaps a recent update had caused it to change state. In any event, that was causing network manager to shut down the connection as soon as it had been established, causing a "device state change" and forming an infinite loop!

Clearing the checkbox stopped it. I'm marking this solved in case anyone else runs into a similar situation, unlikely though that may be.

---

