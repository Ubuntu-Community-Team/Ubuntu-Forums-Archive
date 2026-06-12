---
title: "ERROR: daemon: command not found"
date: 2008-01-06
forum: General Help
---

### Post by NoSkill on 2008-01-06
Hi I'm putting together a init.d script for perforce:

```
#!/bin/sh -e
  export P4JOURNAL=/var/log/perforce/journal
  export P4LOG=/var/log/perforce/p4err
  export P4ROOT=/perforce_depot
  export P4PORT=1666

  PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

  . /lib/lsb/init-functions

  p4start="p4d -d"
  p4stop="p4 admin stop"
  p4user=perforce

  case "$1" in
  start)
    log_action_begin_msg "Starting Perforce Server"
    daemon -u $p4user $p4start;
    ;;

  stop)
    log_action_begin_msg "Stopping Perforce Server"
    daemon -u $p4user $p4stop;
    ;;

  restart)
    stop
    start
    ;;

  *)
    echo "Usage: /etc/init.d/perforce (start|stop|restart)"
    exit 1
    ;;

esac

```

When i try to start the script with /etc/init.d/perforce start I get the following error

 * Starting Perforce Server...                                                 
 /etc/init.d/perforce: line 18: daemon: command not found

Any ideas on how to fix this?

Thanks

---

### Post by geraldm on 2008-01-07
Looks like you need to find an executable named "daemon" or else change the lines that use that command.
debian systems use start-stop-daemon.  See the manpage for that.

Gerald

---

