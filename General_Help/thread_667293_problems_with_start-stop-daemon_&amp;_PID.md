---
title: "problems with start-stop-daemon &amp; PID"
date: 2008-01-14
forum: General Help
---

### Post by viggeh on 2008-01-14
**Short version:** start-stop-daemon doesn't save a PID file for the process it started unless the -m switch is provided, in which case the PID in the file is incorrect.

**Long version:** Three days ago I decided to turn an old computer into a server (apache, php, mysql, ftp, ssh, possibly some game server aswell) and decided to go with ubuntu-server as I've never used linux before. It took some time to install everything and get used to the ssh terminal and vi but I'm getting there. However, I've run into a problem (one of many of course, but I've been able to solve the other ones so far); starting/stopping/restarting proftpd through the init.d script doesn't work very well. The original script didn't use start-stop-daemon and wasn't creating any pid file so I rewrote the whole thing based on the init.d script for ddclient (which used start-stop-daemon). My own version now looks like this:
```
#!/bin/bash

# Configuration
NAME="proftpd"
DAEMON=/usr/local/sbin/proftpd
PIDFILE=/var/run/$NAME.pid
OPTIONS="-c /etc/proftpd.conf"

# log_* functions
. /lib/lsb/init-functions


if [ ! -x $DAEMON ]; then
  log_warning_msg "$0: $DAEMON: cannot execute"
  log_end_msg 1
  exit 1
fi

do_start()
{
        #Returns
        # 0 = started
        # 1 = already running
        # 2 = could not be started
        start-stop-daemon --test --start  \
                          --pidfile $PIDFILE --name $NAME --startas $DAEMON \
                >/dev/null \
                || return 1
        start-stop-daemon --start --quiet \
                          --pidfile $PIDFILE --name $NAME --startas $DAEMON \
                || return 2
}

do_stop()
{
        #Returns
        # 0 = stopped
        # 1 = already stopped
        # 2 = could not be stopped
        start-stop-daemon --stop --quiet \
                          --pidfile $PIDFILE --name $NAME
        return "$?"
}

case $1 in

  start)
    log_daemon_msg "Starting $NAME"
    do_start
    case "$?" in
         0) log_end_msg 0 ;;
         1) log_warning_msg "- already started"
            log_end_msg 0 ;;
         2) log_end_msg 1 ;;
    esac
    ;;

  stop)
    log_daemon_msg "Stopping $NAME"
    do_stop
    case "$?" in
         0) log_end_msg 0 ;;
         1) log_warning_msg "- already stopped"
            log_end_msg 0 ;;
         2) log_end_msg 1 ;;
    esac
    ;;

  restart)
    log_daemon_msg "Restarting $NAME"
    do_stop
    case "$?" in
         0|1)
             do_start
             case "$?" in
                 0) log_end_msg 0 ;;
                 1) log_end_msg 1 ;; # Old process is still running
                 *) log_end_msg 1 ;; # Failed to start
             esac
             ;;
         *)
             # Failed to stop
             log_end_msg 1
             ;;
    esac
    ;;

  *)
    echo "usage: $0 {start|stop|restart}"
    exit 1
    ;;

esac

exit 0
```

I've been stuck for over three hours trying to get this to work, without success. With the above script no PID file is created at all, but if I turn on the -m switch in the start process it is created. In this case, however, the PID contained in the file is incorrect (example: PID of proftpd: 4443, PID reported in file: 4464). Any ideas what's causing this or how to solve it?

Thanks in advance, I'm getting tired of this one =/

---

### Post by jivetolkein on 2008-06-05
resurrecting this thread as I have the same problem (different script of my own writing)..

start-stop-daemon creates the pid file but the actual executable runs as a different pid.

---

