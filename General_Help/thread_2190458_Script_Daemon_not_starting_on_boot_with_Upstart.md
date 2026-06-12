---
title: "Script Daemon not starting on boot with Upstart"
date: 2013-11-27
forum: General Help
---

### Post by mjpsr11 on 2013-11-27
My daemon script is not working after reboot. The script file is located in the /etc/init.d folder with the following heading:

```
#! /bin/sh

### BEGIN INIT INFO
# Provides:          timekpr
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Timekpr - Keep control of computer usage
# Description:       This program will track and control the computer usage
#                    of your kids. You can limit their daily usage and
#                    configure periods when they cannot log in.
### END INIT INFO
```

Links are also located properly in /etc/rc*.d folders.  The script works fine with  [COLOR=#0000BF]sudo bash /etc/init.d/timekpr [start|restart][/COLOR]

After  reboot, the file /var/run/timekpr.pid exists with a pid, but that pid  is not a running process. It seems that during boot, the script may be  working and creates a process, but then somehow kills the process before  completing the boot.

I've tried this on Ubuntu and now Mint distros with no luck. I somehow got it to work on the Zorin distro.

---

### Post by oldos2er on 2013-11-27
Moved to General Help.

---

