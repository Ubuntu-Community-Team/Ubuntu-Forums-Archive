---
title: "Determining reboot reason"
date: 2013-03-05
forum: General Help
---

### Post by mc0001 on 2013-03-05
Hi,
A server running 12.04 recently rebooted itself, but looking in the files in /var/log doesn't show any reason, e.g. OOM killer events, etc. Is there any way that one can discern why a machine rebooted itself?
TIA

---

### Post by lechien73 on 2013-03-05
Hi,

```
last -x
```

will display the last shutdown events from wtmp, so although it won't give you a reason, it will give you the times so that you can try look for events in the logs that correspond with the exact time of the last reboot.

---

### Post by mc0001 on 2013-03-05
Hi lechien73,
Thanks for the info. The corresponding snippet from "last -x" would be:

runlevel (to lvl 2)   3.2.0-38-generic Tue Mar  5 08:50 - 11:59  (03:09)    
reboot   system boot  3.2.0-38-generic Tue Mar  5 08:50 - 11:59  (03:09)    
runlevel (to lvl 0)   3.2.0-38-generic Tue Mar  5 08:47 - 08:50  (00:02)    

The only related event in the syslog file for that time is:

Mar  5 08:47:58 node87 kernel: [262411.141613] init: idmapd main process (1120) killed by TERM signal
Mar  5 08:47:58 node87 kernel: Kernel logging (proc) stopped.
Mar  5 08:47:58 node87 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1165" x-info="http://www.rsyslog.com"] exiting on signal 15.

This machine is an NFS4 client, with idmapd enabled, and performs lots of reads off a server, causing some processes to go into uninterruptible sleep at times. However, I can't see how that would cause anything to panic on a client, forcing a reboot.

---

### Post by ali abry on 2013-03-05
PIDs killed with signal 15 which means that they killed nicely without any force. so its not look like a sudden reboot or something it's more like a normal reboot.
did you check  the boot log. if there was problem maybe in there  you can find something related to it .

---

