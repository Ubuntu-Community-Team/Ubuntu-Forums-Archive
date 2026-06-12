---
title: "service returns unknown job"
date: 2018-02-26
forum: General Help
---

### Post by HiRez_L on 2018-02-26
So, I installed some new software, radarr, and set it up as a service.  After putting the script for the service in /etc/init.d, chmod'ing it to 755, and running update-rc.d on it, I tried to start the service:

root@REZ:/etc/init.d# service radarr status
status: Unknown job: radarr
root@REZ:/etc/init.d# service radarr start
start: Unknown job: radarr


Starting it manually with the init script works fine:

root@REZ:/etc/init.d# /etc/init.d/radarr start
Removing stale /var/run/radarr/radarr.pid
Starting Radarr

Although service radarr status returns unknown job, a service --status-all shows the service, with the name radarr, and that it is running:

root@REZ:/etc/init.d# service --status-all
. . .
 [ + ]  radarr
. . .




So what am I doing wrong, why won't it start, stop, or show status using service commands?  This is on an updated Ubuntu 14.04 server.

---

### Post by HiRez_L on 2018-02-26
I saw someone else with a problem like this where the service name was different, so in case there is something in the startup script I am missing, here it is:

```
6root@REZ:/etc/init.d# cat radarr#! /bin/sh
### BEGIN INIT INFO
# Provides: Radarr
# Required-Start: $local_fs $network $remote_fs
# Required-Stop: $local_fs $network $remote_fs
# Should-Start: $NetworkManager
# Should-Stop: $NetworkManager
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: starts instance of Radarr
# Description: starts instance of Radarr using start-stop-daemon
### END INIT INFO


############### EDIT ME ##################
# path to app
APP_PATH=/opt/Radarr


# user
RUN_AS=root


# path to mono bin
DAEMON=$(which mono)


# Path to store PID file
PID_FILE=/var/run/radarr/radarr.pid
PID_PATH=$(dirname $PID_FILE)


# script name
NAME=radarr


# app name
DESC=Radarr


# startup args
EXENAME="Radarr.exe"
DAEMON_OPTS=" "$EXENAME


############### END EDIT ME ##################


RADARR_PID=`ps auxf | grep Radarr.exe | grep -v grep | awk '{print $2}'`


test -x $DAEMON || exit 0


set -e


#Look for PID and create if doesn't exist
if [ ! -d $PID_PATH ]; then
    mkdir -p $PID_PATH
    chown $RUN_AS $PID_PATH
fi


if [ ! -d $DATA_DIR ]; then
    mkdir -p $DATA_DIR
    chown $RUN_AS $DATA_DIR
fi


if [ -e $PID_FILE ]; then
    PID=`cat $PID_FILE`
    if ! kill -0 $PID > /dev/null 2>&1; then
        echo "Removing stale $PID_FILE"
        rm $PID_FILE
    fi
fi


echo $RADARR_PID > $PID_FILE


case "$1" in
    start)
        if [ -z "${RADARR_PID}" ]; then
            echo "Starting $DESC"
            rm -rf $PID_PATH || return 1
            install -d --mode=0755 -o $RUN_AS $PID_PATH || return 1
            start-stop-daemon -d $APP_PATH -c $RUN_AS --start --background --pidfile $PID_FILE --exec $DAEMON -- $DAEMON_OPTS
        else
            echo "Radarr already running."
        fi
    ;;
    stop)
        echo "Stopping $DESC"
        echo $RADARR_PID > $PID_FILE
        start-stop-daemon --stop --pidfile $PID_FILE --retry 15
    ;;


    restart|force-reload)
        echo "Restarting $DESC"
        start-stop-daemon --stop --pidfile $PID_FILE --retry 15
        start-stop-daemon -d $APP_PATH -c $RUN_AS --start --background --pidfile $PID_FILE --exec $DAEMON -- $DAEMON_OPTS
    ;;
    status)
        # Use LSB function library if it exists
        if [ -f /lib/lsb/init-functions ]; then
            . /lib/lsb/init-functions
            if [ -e $PID_FILE ]; then
                status_of_proc -p $PID_FILE "$DAEMON" "$NAME" && exit 0 || exit $?
            else
                log_daemon_msg "$NAME is not running"
                exit 3
            fi


        else
            # Use basic functions
            if [ -e $PID_FILE ]; then
                PID=`cat $PID_FILE`
                if kill -0 $PID > /dev/null 2>&1; then
                    echo " * $NAME is running"
                    exit 0
                fi
            else
                echo " * $NAME is not running"
                exit 3
            fi
        fi
    ;;
    *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
        exit 1
    ;;
esac


exit 0
```

---

### Post by wildmanne39 on 2018-02-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by deadflowr on 2018-02-27
Try running just *status job-name* as root
like 
```
#status lightdm
```
of course you being on a server, try a different service.

You can read more up on upstart here:
[http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")
scroll down to Job control for basic start stop status options.

---

### Post by HiRez_L on 2018-02-27
root@REZ:~# status radarr
status: Unknown job: radarr

---

### Post by HiRez_L on 2018-02-27
Went through the upstart link above, and the far longer updated link which it refers one to, and did not glean anything useful from either.  It's like the system just doesn't see the init files in place.

root@REZ:/etc/init.d# update-rc.d radarr defaults
 System start/stop links for /etc/init.d/radarr already exist.
root@REZ:/etc/init.d# service radarr start
start: Unknown job: radarr
root@REZ:/etc/init.d# ls -la rad*
-rwxr-xr-x 1 root root 3005 Feb 26 16:49 radarr
root@REZ:/etc/init# ls -la rad*
-rw-r--r-- 1 root root 304 Feb 26 16:47 radarr.conf


Is having an /etc/init.d/radarr file and an /etc/init/radarr.conf file causing some kind of conflict?

---

### Post by HiRez_L on 2018-03-01
Anyone have anything else to try?

---

### Post by spjackson on 2018-03-01
> **HiRez_L said:**
> Is having an /etc/init.d/radarr file and an /etc/init/radarr.conf file causing some kind of conflict?
The presence of /etc/init/radarr.conf means that the service command doesn't use /etc/init.d/radarr and instead it uses dbus. However, I don't know why the dbus method doesn't work for this particular job.

---

### Post by HiRez_L on 2018-03-01
I'll try temporarily moving radarr out of /etc/init.d and see if that helps.  And vice-versa.

---

### Post by HiRez_L on 2018-03-01
Removing radarr from /etc/init.d didn't help.  I'll put it back and try moving radarr.conf out of /etc/init.

root@REZ:~# mv /etc/init.d/radarr .
root@REZ:~# service radarr status
status: Unknown job: radarr

---

### Post by HiRez_L on 2018-03-01
getting rid of radarr.conf from /etc/init worked!

root@REZ:~# mv radarr /etc/init.d/
root@REZ:~# mv /etc/init/radarr.conf .
root@REZ:~# service radarr status
 * radarr is running
root@REZ:~# service radarr stop
Stopping Radarr
root@REZ:~# service radarr start
Removing stale /var/run/radarr/radarr.pid
Starting Radarr

---

