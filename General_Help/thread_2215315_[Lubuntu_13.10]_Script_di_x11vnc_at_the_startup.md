---
title: "[Lubuntu 13.10] Script di x11vnc at the startup"
date: 2014-04-06
forum: General Help
---

### Post by balubeto on 2014-04-06
Hi

I found this link [https://wiki.edubuntu.org/InstallX11VncOnLtspClients](https://wiki.edubuntu.org/InstallX11VncOnLtspClients) that contains a script for x11vnc to be put in the */etc/init.d* directory. Being an old script, I have transformed the structure into:

```

#!/bin/sh
case "$1" in
        start)
                start-stop-daemon --start --oknodo \
                        --pidfile /var/run/x11vnc.pid --background \
                        --nicelevel 15 --make-pidfile --exec \
                        /usr/bin/x11vnc -rfbport 5900 -auth /var/run/lightdm/root/:0 -rfbauth /etc/x11vnc.pass -nomodtweak -noxrecord -shared -forever -loop -o /var/log/x11vnc.log
        ;;
        stop)
                start-stop-daemon --stop --oknodo --pidfile /var/run/x11vnc.pid
        ;;
        restart)
                $0 stop
                $0 start
        ;;
        *)
                echo "Usage: $0 start|stop|restart"
        ;;
esac
exit 0

```

So I wrote the *sudo chmod 755 /etc/init.d/x11vnc* and *sudo ln -s /etc/init.d/x11vnc /etc/rc2.d/S99x11vnc* commands. indeed:

```

lrwxrwxrwx 1 root root 18 apr  4 19:21 /etc/rc2.d/S99x11vnc -> /etc/init.d/x11vnc

```

The commands to create the password, I do not have them done because I had them already made&#8203;&#8203;. So, I rebooted the machine, but the x11vnc server is not started and, moreover, it has not created any log file. 

So, I tried to run the command *sudo /etc/init.d/x11vnc start * and its ouput is:

```

start-stop-daemon: invalid option -- 'f'

```

How come?

Thanks

Bye

---

### Post by balubeto on 2014-04-07
I created this script:

```

#! /bin/sh
#
### BEGIN INIT INFO
# Provides: x11vnc
# Required-Start: $syslog $local_fs
# Required-Stop: $syslog $local_fs
# Should-Start: LightDM
# Default-Start: 2
# Default-Stop: 1
# Short-Description: x11 vnc
# Description: x11vnc
### END INIT INFO
DAEMON=/usr/bin/x11vnc
NAME=x11vnc
DESC="X11 vnc"
test -x $DAEMON || exit 0
DAEMON_OPTS="-auth /var/run/lightdm/root/:0 -rfbauth /etc/x11vnc.pass -nomodtweak -shared -forever -o /var/log/x11vnc.log -bg"
set -e
 case "$1" in
           start)
                   echo -n "Starting $DESC: "
                   start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
                                                     --exec $DAEMON -- $DAEMON_OPTS &
                   echo "$NAME."
           ;;
           stop)
                   echo -n "Stopping $DESC: "
                   start-stop-daemon --stop --oknodo --quiet --pidfile /var/run/$NAME.pid \
                                                    --exec $DAEMON
                   echo "$NAME."
           ;;
           restart)
                      echo -n "Restarting $DESC: "
                      start-stop-daemon --stop --quiet --pidfile \
                      /var/run/$NAME.pid --exec $DAEMON
                      sleep 1
                      start-stop-daemon --start --quiet --pidfile \
                      /var/run/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS
                      echo "$NAME."
          ;;
          status)
                     if [ -s /var/run/$NAME.pid ]; then
                        RUNNING=$(cat /var/run/$NAME.pid)
                        if [ -d /proc/$RUNNING ]; then
                            if [ $(readlink /proc/$RUNNING/exe) = $DAEMON ]; then
                                echo "$NAME is running."
                                exit 0
                            fi
                        fi
                        # No such PID, or executables don't match
                        echo "$NAME is not running, but pidfile existed."
                        rm /var/run/$NAME.pid
                        exit 1
                     else
                           rm -f /var/run/$NAME.pid
                           echo "$NAME not running."
                           exit 1
                     fi
          ;;
          *)
            N=/etc/init.d/$NAME
            echo "Usage: $N {start|stop|restart|force-reload}" >&2
            exit 1
           ;;
 esac
exit 0

```

and I saved in */etc/init.d/x11vnc* and, apparently, it works and I can also control the LightDM.

Now, I continue in my main thread[http://ubuntuforums.org/showthread.php?t=2212640](http://ubuntuforums.org/showthread.php?t=2212640) .

Thanks

Bye

---

