---
title: "/etc/init.d service startup script"
date: 2015-11-19
forum: General Help
---

### Post by dr34mup on 2015-11-19
Hello all,

I am trying to make my first startup script for the programm Glassfish.
At the moment you need to use this to start, stop and restart the program:

```

/opt/glassfish/bin/asadmin start-domain
/opt/glassfish/bin/asadmin stop-domain
/opt/glassfish/bin/asadmin restart-domain

```

So this is like my script looks right now:

```

#!/bin/sh


### BEGIN INIT INFO
#
# Provides:        glassfish
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:    $local_fs $remote_fs $network
# Default-Start:    2 3 4 5
# Default-Stop:        0 1 6
# Short-Description:    Glassfish scipt (Non official)
# Description:    Start Glassfish domain as service.
#
### END INIT INFO


# Using the LSB functions to perform the operations
. /lib/lsb/init-functions


BASE=/opt/glassfish/bin
NAME=glassfish
DAEMON=${BASE}/asadmin
SCRIPTNAME=/etc/init.d/$NAME


#PID file for the daemon
PIDFILE=/var/run/glassfish.pid


#If the daemon is not there, then exit
[ -x "$DAEMON" ] || exit 5


do_start()
{
        start-stop-daemon --start --quiet --make-pidfile --pidfile $PIDFILE --exec $DAEMON -- start-domain
}


do_stop()
{
    start-stop-daemon --stop --quiet --pidfile $PIDFILE
}


case $1 in
    start)
        #Check PID file
        if [ -e $PIDFILE ]; then
            status_of_proc -p $PIDFILE "$NAME process" && status="0" || status="$?"
            # IF SUCCESS dont start again
            if [ $status = "0" ]; then
                exit
            fi
        fi


        #Start the daemon
        log_daemon_msg "Starting the process" "$NAME"
        if do_start; then
            log_end_msg 0
        else
            log_end_msg 1
        fi
        ;;


    stop)
        # Stop the daemon
        if [ -e $PIDFILE ]; then
            status_of_proc -p $PIDFILE $DAEMON "Stopping the $NAME process" && status="0" || status="$?"
            if [ "$status" = 0]; then
                do_stop
            fi
        else
            log_daemon_msg "$NAME process is not running"
            log_end_msg 0
        fi
        ;;


    restart)
        # Restart the daemon
            $0 stop && sleep 2 && $0 start
        ;;


    status)
        # Check status
        if [ -e $PIDFILE ]; then
            status_of_proc -p $PIDFILE $DAEMON "$NAME process" && exit 0 || exit $?
        else
            log_daemon_msg "$NAME Process is not running"
            log_end_msg 0
        fi
        ;;


    *)
        # Show help
        echo "Usage: $SCRIPTNAME {start|stop|restart}" >&2
        exit 3
        ;;
esac

```

(First he didn't created the PID file so I have to set the parameter '--make-pidfile' since the Java Glassfish didn't created it.)

The PID gets now created but the output on status or stop is that there is no PID file existing. I try to get this working since yesterday.

Maybe someone can help me and tell me what I am doing wrong?

---

### Post by dr34mup on 2015-11-19
Starting the service also not works:

```

 sudo /etc/init.d/glassfish start
[sudo] password for administrator:
 * glassfish process is not running
 * Starting the process glassfish                                                                                                                                                                                                           
 There is a process already using the admin port 4848 -- it probably is another instance of a GlassFish server.
Command start-domain failed.



```

And stopping:

```

sudo /etc/init.d/glassfish stop
 * Stopping the glassfish process is not running
/etc/init.d/glassfish: 64: [: missing ]

```

But the file exists:

```

 ls /var/run/glass*
/var/run/glassfish.pid

```

I don't get it...

---

### Post by dr34mup on 2015-11-19
I can not believe. Finally I get it working!
If someone is interested here is the full script. (Including some useless comments for me to understand)

```

#!/bin/sh


### BEGIN INIT INFO
#
# Provides:        glassfish
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:    $local_fs $remote_fs $network
# Default-Start:    2 3 4 5
# Default-Stop:        0 1 6
# Short-Description:    Glassfish scipt (Non official)
# Description:    Start Glassfish domain as service.
#        Non official startup script by Bernhard Sumser.
#
### END INIT INFO


# Using the LSB functions to perform the operations
# NOT needed because no LSB functions used
#. /lib/lsb/init-functions


BASE=/opt/glassfish/bin
NAME=glassfish
DAEMON=${BASE}/asadmin
SCRIPTNAME=/etc/init.d/$NAME


#PID file for the daemon
PIDFILE=/var/run/glassfish.pid


#If the DAEMON is not there, then exit
[ -x "$DAEMON" ] || exit 0




do_start()
{
    $DAEMON start-domain &
    # Wait for child to exit before continuing
    wait
    # Make file with last background PID
    echo $! > $PIDFILE


    # Didn't work because the programm prints from the background. Without moving to the bg no $! can be outputed to file
    #(($DAEMON start-domain) & echo $! > $PIDFILE &)
}


do_stop()
{
    $DAEMON stop-domain
    if [ -e $PIDFILE ]; then
        rm -f $PIDFILE
    fi
}


check_root()
{
    if [ "$(id -u)" != "0" ]; then
        echo "You must be root to start, stop and restart $NAME."
        exit 4
    fi
}


check_process()
{
    # Check if the process is already running. Ignore grep line.
    result=`ps aux | grep /opt/glassfish/modules/glassfish.jar | grep -v grep | wc -l`
}


case $1 in
    start)
        check_root
        check_process
        if [ "$result" = "1"  ]; then
            echo "$NAME is already running"
        else
            # Check if PID file exists and delete it
            if [ -e $PIDFILE ]; then
                rm -f $PIDFILE
            else
                do_start
            fi                
        fi
    ;;


    stop)
        check_root
        if [ -e $PIDFILE ]; then
            do_stop
        else
            echo "$NAME is not running"
        fi
    ;;


    restart)
        check_root
        echo "Restarting $NAME..."
        check_process
        if [ "$result" = "1"  ]; then
            do_stop
            echo "Starting $NAME..."
            do_start
        fi                    
    ;;


    status)
        if [ -e $PIDFILE ]; then
            echo "$NAME is running. PID $(cat $PIDFILE)"
        else
            echo "$NAME is not running"
        fi
    ;;




    *)
            # Show help
            echo "Usage: $SCRIPTNAME {start|status|stop|restart}" >&2
            exit 3
    ;;
esac



```

I am not sure if the INIT Info is needed. Because I registered it as service and for the runlevel startup I will not do any more changes.

---

