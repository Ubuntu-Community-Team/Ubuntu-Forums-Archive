---
title: "rkhunter results. Am I safe?"
date: 2007-12-14
forum: General Help
---

### Post by zbtgs on 2007-12-14
[20:53:49]   Checking for running syslog daemon              [ Warning ]
[20:53:49] Warning: The syslog daemon is not running.
[20:53:49]   Checking for syslog configuration file          [ Found ]
[20:53:49] Info: Found syslog configuration file: /etc/syslog.conf
[20:53:49]   Checking if syslog remote logging is allowed    [ Not allowed ]

[20:54:08]   Checking /dev for suspicious file types         [ None found ]
[20:54:09]   Checking for hidden files and directories       [ Warning ]
[20:54:09] Warning: Hidden directory found: /dev/.static
[20:54:09] Warning: Hidden directory found: /dev/.udev
[20:54:09] Warning: Hidden directory found: /dev/.initramfs
[20:54:09] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)

---

### Post by bodhi.zazen on 2007-12-14
The only safe computer is one that is turned off, disconnected from the network, and locked in a vault.

Those rkhunter results are not a problem.

There are a few threads on this topic here :

[http://ubuntuforums.org/showthread.php?t=483016](http://ubuntuforums.org/showthread.php?t=483016)

---

