---
title: "[Tremulous] - init.d script not quiet"
date: 2008-02-10
forum: General Help
---

### Post by mcdesign on 2008-02-10
Hello,

I made my own init.d boot script for a tremulous server, but when i boot i still see the output of my script.
 
The source of the init.d script:
```

#!/bin/bash

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
DAEMON="/home/administrator/noobforce/tremulous/tremded.x86"
OPTIONS="+set dedicated 2 +exec server.cfg"
NAME="tremulous-server"
DESC="Tremulous dedicated server"
PIDFILE="/var/run/$NAME.pid"

test -x $DAEMON || exit 5

. /lib/lsb/init-functions

if [ -f /etc/default/tremulous-server ] ; then
	. /etc/default/tremulous-server
fi

set -e

tremulous_start() { 
        if [ -f $PIDFILE ]; then 
                return 2 
        else 
                start-stop-daemon --start --quiet --pidfile $PIDFILE --oknodo \ --background --exec $DAEMON $OPTIONS --make-pidfile  
                        --$DAEMON_OPTS &> /dev/null || return 1 
        fi 

        return 0 
}

tremulous_stop() {
    start-stop-daemon --stop --quiet --pidfile $PIDFILE \
	--oknodo || return 1
    rm -f $PIDFILE
    return 0
}

case "$1" in
    start)
        log_begin_msg "Starting $DESC: $NAME"
        tremulous_start
        log_end_msg $?
	;;
    stop)
        log_begin_msg "Stopping $DESC: $NAME"
        tremulous_stop
        log_end_msg $?
	;;
    #reload)

	# echo "Reloading $DESC configuration files."
	# start-stop-daemon --stop --signal 1 --quiet --pidfile \
	#	/var/run/$NAME.pid --exec $DAEMON
        #;;
    restart|force-reload)

        log_begin_msg "Restarting $DESC: $NAME"
        tremulous_stop && sleep 1 && tremulous_start
        log_end_msg $?
	;;
    *)
	# echo "Usage: $0 {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $0 {start|stop|restart|force-reload}" >&2
	exit 1
	;;
esac

exit 0

```

Do you know a solution, or should i stop making init.d scripts because i'm too stupid for it ? :(

Greets,
Martin

---

