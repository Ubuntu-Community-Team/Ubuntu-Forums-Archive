---
title: "ntpd do not update time"
date: 2007-07-06
forum: General Help
---

### Post by dpchemist on 2007-07-06
Hello all!

Couple days ago I noticed that desktop running Dapper for ~1 year has clock time deviation ~6 min from standard time. When I had tried to restart ntp with command
```
sudo /etc/init.d/ntp-server restart
```
it reported to be restarted, however, ntpq -p gave me
```
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 fiordland.ubunt .INIT.          16 u    -   64    0    0.000    0.000 4000.00
 h-64-105-110-66 .INIT.          16 u    -   64    0    0.000    0.000 4000.00
 ecmail1.cmc.ec. .INIT.          16 u    -   64    0    0.000    0.000 4000.00
 molecule.ecn.pu .INIT.          16 u    -   64    0    0.000    0.000 4000.00
 10.10.10.10     .INIT.          16 u    -   64    0    0.000    0.000 4000.00
 ntp-public.uit. .INIT.          16 u    -   64    0    0.000    0.000 4000.00
```
and no time adjustment occured for couple days since then.

When I am restarting ntp I have following in a syslog:
```
Jul  6 20:18:35 localhost ntpd[26451]: ntpd 4.2.0a@1:4.2.0a+stable-8-r Mon May 29 02:48:41 UTC 2006 (1)
Jul  6 20:18:35 localhost ntpd[26451]: precision = 2.000 usec
Jul  6 20:18:35 localhost ntpd[26451]: Listening on interface wildcard, 0.0.0.0#123
Jul  6 20:18:35 localhost ntpd[26451]: Listening on interface wildcard, ::#123
Jul  6 20:18:35 localhost ntpd[26451]: Listening on interface lo, 127.0.0.1#123
Jul  6 20:18:35 localhost ntpd[26451]: Listening on interface eth0, 192.168.2.6#123
Jul  6 20:18:35 localhost ntpd[26451]: kernel time sync status 0040
Jul  6 20:18:35 localhost ntpd[26451]: frequency initialized 0.000 PPM from /var/lib/ntp/ntp.drift
Jul  6 20:18:49 localhost **ntpd_initres[26220]: parent died before we finished, exiting**
```

Any ideas how to get ntp working?

ntp.conf is attached

Thanks in advance,
D.

---

### Post by dcstar on 2007-07-07
> **dpchemist said:**
> Hello all!

Couple days ago I noticed that desktop running Dapper for ~1 year has clock time deviation ~6 min from standard time. When I had tried to restart ntp with command
........
Thanks in advance,
D.

You don't need to run a NTP server to keep a machine synced (only if you want **other** machines to use you as a reference), just right-click the Gnome time display and select an appropriate time server in the "Adjust Date and Time" section.

---

