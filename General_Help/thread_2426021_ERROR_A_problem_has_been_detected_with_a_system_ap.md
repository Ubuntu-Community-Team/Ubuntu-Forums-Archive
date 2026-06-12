---
title: "ERROR: A problem has been detected with a system application."
date: 2019-09-03
forum: General Help
---

### Post by felixbischoff on 2019-09-03
Every time I boot the system the error message: "A problem has been detected with a system application." appears.

apport.log:
```
ERROR: apport (pid 22433) Fri Aug 23 21:23:21 2019: called for pid 3006, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 22433) Fri Aug 23 21:23:21 2019: executable: /usr/bin/dbus-daemon (command line "/usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only")
ERROR: apport (pid 22433) Fri Aug 23 21:23:27 2019: gdbus call error: Error connecting: Error receiving data: Connection reset by peer


ERROR: apport (pid 22433) Fri Aug 23 21:23:27 2019: debug: session gdbus call: 
ERROR: apport (pid 22433) Fri Aug 23 21:23:27 2019: wrote report /var/crash/_usr_bin_dbus-daemon.1000.crash
ERROR: apport (pid 9761) Sun Aug 25 02:50:07 2019: called for pid 3096, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 9761) Sun Aug 25 02:50:07 2019: executable: /usr/bin/dbus-daemon (command line "/usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only")
ERROR: apport (pid 9761) Sun Aug 25 02:50:13 2019: gdbus call error: Error connecting: Error receiving data: Connection reset by peer


ERROR: apport (pid 9761) Sun Aug 25 02:50:13 2019: debug: session gdbus call: 
ERROR: apport (pid 9761) Sun Aug 25 02:50:13 2019: wrote report /var/crash/_usr_bin_dbus-daemon.1000.crash
ERROR: apport (pid 31003) Sun Aug 25 17:48:58 2019: called for pid 2982, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 31003) Sun Aug 25 17:48:58 2019: executable: /usr/bin/dbus-daemon (command line "/usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only")
ERROR: apport (pid 31003) Sun Aug 25 17:49:03 2019: gdbus call error: Error connecting: Error receiving data: Connection reset by peer


ERROR: apport (pid 31003) Sun Aug 25 17:49:03 2019: debug: session gdbus call: 
ERROR: apport (pid 31003) Sun Aug 25 17:49:03 2019: this executable already crashed 2 times, ignoring
```

---

### Post by Xian on 2019-09-04
These may just be previously reported errors that are getting recycled. 

First just remove the crash reports:

$ sudo rm /var/crash/*

Does the issue still persist?

---

### Post by felixbischoff on 2019-09-05
Looks good. Thanks):P

---

### Post by Buntu Bunny on 2019-09-09
Thanks from me too, Xian. I was having the same problem and this worked for me as well.

---

