---
title: "how do I run a script at suspend using network"
date: 2016-11-21
forum: General Help
---

### Post by adh9w on 2016-11-21
I'd like to run a backup script when I suspend my desktop.  The script uses rsync over ssh.  The problem is, the network is unreachable when I run the script.  I tried incorporating the solution from post #15 of [https://ubuntuforums.org/showthread.php?t=2157585&page=2](https://ubuntuforums.org/showthread.php?t=2157585&page=2) but I still am unable to connect to the network in the script.  I'm running Ubuntu 14.04LTS

Here's the script I placed in /etc/pm/sleep.d/00_businessBackup.sh  (It's executable and owned by root.)

#!/bin/bash


case "$1" in
    suspend)
        sleep 3
        service network-manager restart
        sleep 20 
               rsync -a --log-file=/root/businessBackup.log /home/aaron/Documents/Business root@192.168.1.2:/mnt/usb-garage/
esac

Here's the pertinent section of /var/log/pm-suspend.log

...
Running hook /etc/pm/sleep.d/00_businessBackup.sh suspend suspend:
network-manager stop/waiting
network-manager start/running, process 30876
connect: Network is unreachable
ssh: connect to host 192.168.1.2 port 22: Network is unreachable
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(226) [sender=3.1.0]
/etc/pm/sleep.d/00_businessBackup.sh suspend suspend: Returned exit code 255.


Mon Nov 21 08:36:48 EST 2016: Inhibit found, will not perform suspend
Mon Nov 21 08:36:48 EST 2016: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:
/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.


Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.

---

