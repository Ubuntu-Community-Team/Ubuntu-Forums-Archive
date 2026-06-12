---
title: "Problems with PID file and start-stop-daemon"
date: 2007-02-23
forum: General Help
---

### Post by halcyon943 on 2007-02-23
Hi,

I'm using the start-stop-daemon to start and stop Barnyard on Ubuntu
6.06 server install.  The start-up script will start Barnyard without
any problems, but it cannot stop it properly.  The reason being it
writes the wrong PID to the PID file, so when it looks at that PID
file it tries to kill a different process ID(e.g.: ps says barnyard is
5056, but cat barn.pid gives 5026).  Below is the start and stop of my
script: 

```
#!/bin/bash

. /lib/lsb/init-functions

barn_opt=' -c /etc/snort/barnyard.conf -g /etc/snort/gen-msg.map -s /etc/snort/sid-msg.map -d /var/log/snort -f snort.log -w /etc/snort/bylog.waldo&'

case "$1" in
        start)
                log_begin_msg "Starting Barnyard 0.2.0..."
                start-stop-daemon --start --quiet --background --make-pidfile --pidfile /var/lock/barn.pid --exec /usr/local/bin/barnyard --$barn_opt || log_end_msg 1
                log_end_msg 0
                ;;
        stop)
                log_begin_msg "Stopping Barnyard 0.2.0..."
                start-stop-daemon --stop  --oknodo --retry 30 --pidfile /var/lock/barn.pid --name barnyard || log_end_msg 1
                log_end_msg 0
                ;; 
```

The odd thing is I have the same exact script on another box and it
works perfectly.  Both systems have been updated with the latest
patches.  Any help or ideas would be greatly appreciated and thanks in
advance for the help.

---

