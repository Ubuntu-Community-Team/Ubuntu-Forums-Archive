---
title: "Ubuntu 10.04 Reboot randomly"
date: 2014-10-01
forum: General Help
---

### Post by alessandro19 on 2014-10-01
only today 30 september i had 4 reboot. I made the cuts in /var/log/messages and I noticed that there are always  reboot when  starts " kjournald starting" , will be a case?
  This is my "last reboot";

```
[INDENT]reboot   system boot  2.6.32-33-generi Tue Sep 30 01:20 - 16:21  (15:01)    
reboot   system boot  2.6.32-33-generi Tue Sep 30 01:07 - 16:21  (15:14)    
reboot   system boot  2.6.32-33-generi Tue Sep 30 00:48 - 16:21  (15:33)    
reboot   system boot  2.6.32-33-generi Tue Sep 30 00:42 - 16:21  (15:39) 
[/INDENT]
 
```

  **cut Log /var/log/messages at 00:48**

  ```
Sep 30 00:42:00 node3 kernel: [   14.479349] kjournald starting.  Commit interval 5 seconds
Sep 30 00:42:00 node3 kernel: [   14.480166] EXT3 FS on sdc1, internal journal
Sep 30 00:42:00 node3 kernel: [   14.480171] EXT3-fs: mounted filesystem with ordered data mode.
Sep 30 00:42:00 node3 kernel: [   14.510855] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
Sep 30 00:42:00 node3 kernel: [   14.524286] type=1505 audit(1412030520.401:11):  operation="profile_load" pid=969 name="/usr/share/gdm/guest-session/Xsession"
Sep 30 00:42:00 node3 kernel: [   14.592014] igb: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
Sep 30 00:42:00 node3 kernel: [   14.635612] igb: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Sep 30 00:42:02 node3 kernel: [   16.710605] svc: failed to register lockdv1 RPC service (errno 97).
Sep 30 00:38:27 node3 kernel: [   18.221194] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Sep 30 00:38:27 node3 kernel: [   18.261212] NFSD: starting 90-second grace period
Sep 30 00:38:28 node3 kernel: [   19.038733] NET: Registered protocol family 5
Sep 30 00:48:00 node3 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 30 00:48:00 node3 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="927" x-info="http://www.rsyslog.com"] (re)start
Sep 30 00:48:00 node3 rsyslogd: rsyslogd's groupid changed to 103
Sep 30 00:48:00 node3 rsyslogd: rsyslogd's userid changed to 101
Sep 30 00:48:00 node3 kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 30 00:48:00 node3 kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 30 00:48:00 node3 kernel: [    0.000000] Linux version 2.6.32-33-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 (Ubuntu 2.6.32-33.70-generic 2.6.32.41+drm33.18)
Sep 30 00:48:00 node3 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=367fc239-c886-467a-80c3-5e49806c881d ro quiet splash
```

**cut Log /var/log/messages at 01:07**
  
```
Sep 30 00:48:00 node3 kernel: [   14.679832] kjournald starting.  Commit interval 5 seconds
Sep 30 00:48:00 node3 kernel: [   14.680665] EXT3 FS on sdc1, internal journal
Sep 30 00:48:00 node3 kernel: [   14.680671] EXT3-fs: mounted filesystem with ordered data mode.
Sep 30 00:48:00 node3 kernel: [   14.711546] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
Sep 30 00:48:00 node3 kernel: [   14.717581] type=1505 audit(1412030880.591:11):  operation="profile_load" pid=984 name="/usr/share/gdm/guest-session/Xsession"
Sep 30 00:48:00 node3 kernel: [   14.810793] igb: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
Sep 30 00:48:00 node3 kernel: [   14.854637] igb: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Sep 30 00:48:02 node3 kernel: [   16.957842] svc: failed to register lockdv1 RPC service (errno 97).
Sep 30 00:48:03 node3 kernel: [   17.361286] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Sep 30 00:44:26 node3 kernel: [   17.393769] NFSD: starting 90-second grace period
Sep 30 00:44:27 node3 kernel: [   18.548975] NET: Registered protocol family 5
Sep 30 00:51:46 node3 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="927" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Sep 30 01:07:00 node3 kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep 30 01:07:00 node3 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="894" x-info="http://www.rsyslog.com"] (re)start
Sep 30 01:07:00 node3 rsyslogd: rsyslogd's groupid changed to 103
Sep 30 01:07:00 node3 rsyslogd: rsyslogd's userid changed to 101
Sep 30 01:07:00 node3 kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 30 01:07:00 node3 kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 30 01:07:00 node3 kernel: [    0.000000] Linux version 2.6.32-33-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 (Ubuntu 2.6.32-33.70-generic 2.6.32.41+drm33.18)
Sep 30 01:07:00 node3 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=367fc239-c886-467a-80c3-5e49806c881d ro quiet splash
```

[B]The cut Log at 01:20 is the same others


Help me?
[/B]

---

### Post by ian-weisser on 2014-10-01
Those logs seem to be post-reboot.
It would be helpful to know if any warning pop up in the logs before reboot.

Ubuntu doesn't randomly reboot without warning. The reboot and shutdown command(s) that I know about would leave a log entry and warn logged-in users. The system is supposed to be shut down gracefully.
Hardware faults, however, can cause random reboots. Have you looked at overheating? Power loss?

---

### Post by Bucky Ball on 2014-10-01
10.04 LTS has reached end-of-life and is no longer supported by Canonical or these forums (unless you are running the server version and if you are please confirm). Please refer here:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Please back up any valuable data, install a supported release, and post a new thread for any further issues. Thanks and good luck. ;)

---

### Post by codenine75a on 2014-10-01
I like zombie tech.  I would get angry and spit on the floor and then stare at the screen with a look to pummel someone to a tenderized meat condition.  After my little emotional bout with myself, I would download the source code and recompile the service that I think is causing problems.  It may be a naught daemon that is not running like it used to.

---

### Post by Bucky Ball on 2014-10-01
No need to go further with this. Please install a supported release. If you are using 10.04 LTS server, please post in server platforms.

*Thread closed.*

---

