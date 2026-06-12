---
title: "Cannot remove snaps due to change in progress, cannot abort"
date: 2020-06-27
forum: General Help
---

### Post by SpectrumDT on 2020-06-27
Hi! I am running Kubuntu 20.04. I have the following **snap** packages:

```
spectrum@spectrum-desktop:~$ snap list
Name                    Version                  Rev   Tracking       Publisher   Notes
chromium                83.0.4103.61             1165  latest/stable  canonical&#10003;  -
core18                  20200427                 1754  latest/stable  canonical&#10003;  base
foobar2000              1.5.4                    295   latest/stable  mmtrt       -
gtk-common-themes       0.1-36-gc75f853          1506  latest/stable  canonical&#10003;  -
snapd                   2.45                     7777  latest/stable  canonical&#10003;  snapd
spotify                 1.1.26.501.gbe11e53b-15  41    latest/stable  spotify&#10003;    -
wine-platform-5-stable  5.0.1                    5     latest/stable  mmtrt       -
wine-platform-runtime   v1.0                     136   latest/stable  mmtrt       -
```

I want to remove **foobar2000** and **chromium**.

```
spectrum@spectrum-desktop:~$ sudo snap remove foobar2000
[sudo] password for spectrum: 
2020-06-27T10:45:21+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:45:27+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:45:32+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:45:38+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:45:43+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:45:48+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:45:53+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:45:58+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:06+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:11+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:16+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:22+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:27+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:32+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:38+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:43+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:48+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:53+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:46:59+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:47:04+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:47:10+02:00 INFO Waiting for conflicting change in progress...
2020-06-27T10:47:15+02:00 INFO Waiting for conflicting change in progress...
Disconnect interfaces of snap "foobar2000"                                                                           |
2020-06-27T10:47:20+02:00 INFO Waiting for conflicting change in progress...
error: change finished in status "Undone" with no error message
```
**foobar2000** would loop forever with that message until I cancelled it using Ctrl+C.

Now trying to remove **chromium**:

```
spectrum@spectrum-desktop:~$ sudo snap remove chromium  
error: snap "chromium" has "auto-refresh" change in progress
spectrum@spectrum-desktop:~$ snap changes
ID   Status  Spawn                      Ready                    Summary
23   Undone  4 days ago, at 14:53 CEST  yesterday at 16:34 CEST  Auto-refresh snaps "snapd", "chromium", "wine-platform-runtime"
26   Doing   yesterday at 16:34 CEST    -                        Auto-refresh snaps "chromium", "wine-platform-runtime", "snapd"
27   Undone  yesterday at 16:56 CEST    yesterday at 16:56 CEST  Remove "foobar2000" snap
28   Undone  today at 10:45 CEST        today at 10:47 CEST      Remove "foobar2000" snap

spectrum@spectrum-desktop:~$ sudo snap abort 26
spectrum@spectrum-desktop:~$ snap changes
ID   Status  Spawn                      Ready                    Summary
23   Undone  4 days ago, at 14:53 CEST  yesterday at 16:34 CEST  Auto-refresh snaps "snapd", "chromium", "wine-platform-runtime"
26   Abort   yesterday at 16:34 CEST    -                        Auto-refresh snaps "chromium", "wine-platform-runtime", "snapd"
27   Undone  yesterday at 16:56 CEST    yesterday at 16:56 CEST  Remove "foobar2000" snap
28   Undone  today at 10:45 CEST        today at 10:47 CEST      Remove "foobar2000" snap

spectrum@spectrum-desktop:~$ sudo snap remove chromium
error: snap "chromium" has "auto-refresh" change in progress
spectrum@spectrum-desktop:~$
```
It complains about a change in progress. Aborting the change in question does not help. 

Am I doing this wrong? Thanks.

---

### Post by SpectrumDT on 2020-06-27
Related problem: When I shut down my system, it takes a long time to shut down. The shutdown screen says: 

```
A stop job is running for Snap Daemon (... / 1min 30s)
```

This happens on every shutdown, and hangs until the 1 min 30 seconds time out. How can I debug this and figure out why snap hangs?

---

