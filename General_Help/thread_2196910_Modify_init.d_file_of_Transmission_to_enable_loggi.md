---
title: "Modify init.d file of Transmission to enable logging"
date: 2014-01-01
forum: General Help
---

### Post by m1dnight on 2014-01-01
I'm trying to figure out how to enable logging in transission.

I know I can run the daemon in the front:

```
transmission-daemon -f --logfile /your/path/to/transmission.log
```

But this is not what I want. I want to enable this option (log/e) in the service instance. 

So far I've discovered that running ```
sudo service transmission-daemon
``` executes the file located in ```
/etc/init.d/transmission-daemon
```. This file (as shown below) doesn't really make me any wiser.

So far I understand the following:

```
--exec $DAEMON -- $OPTIONS`  executes the effective daemon. This file (as seen in the variable on top of the script) is located in `/usr/bin/$NAME`. `$NAME` is `transmission-daemon
```. This is an executable located in there.

So I think you can pass it along some options (ie --logfile). So I added an instantiation of the OPTIONS variable but this doesn't seem to write anything.

I tried the ```
OPTIONS=" --logfile /smb/torrents/transmission.log"
``` line so that it might append them to the execution but it throws an error.

Another thing I tried was using the option without any quotes.

```
    OPTIONS= -e /smb/torrents/transmission.log
```

This throws me the same error:

```
:~$ sudo service transmission-daemon restart
/etc/init.d/transmission-daemon: 15: /etc/init.d/transmission-daemon: -e /smb/torrents/transmission.log: not found
```

Doing the above without '-' doesn't show me any errors, but doesn't write to the log file either..

Adding the --logfile option after the execution --exec $DAEMON --logfile /path/file -- $OPTIONS yields another error as well:

```
    * Restarting bittorrent daemon transmission-daemon
    start-stop-daemon: unrecognized option '--logfile'
```


The logfile has sufficient permissions, though:

```
    -rwxrwxrwx  1 debian-transmission debian-transmission    0 Dec 30 11:14 transmission.log*
```

So my question is, how do do this exactly?

```
    #!/bin/sh -e
    ### BEGIN INIT INFO
    # Provides:          transmission-daemon
    # Required-Start:    $local_fs $remote_fs $network
    # Required-Stop:     $local_fs $remote_fs $network
    # Default-Start:     2 3 4 5
    # Default-Stop:      0 1 6
    # Short-Description: Start or stop the transmission-daemon.
    ### END INIT INFO
    
    NAME=transmission-daemon
    DAEMON=/usr/bin/$NAME
    USER=debian-transmission
    STOP_TIMEOUT=30
    OPTIONS=" --logfile /smb/torrents/transmission.log"
    
    export PATH="${PATH:+$PATH:}/sbin"
    
    [ -x $DAEMON ] || exit 0
    
    [ -e /etc/default/$NAME ] && . /etc/default/$NAME
    
    . /lib/lsb/init-functions
    
    start_daemon () {
        if [ $ENABLE_DAEMON != 1 ]; then
            log_progress_msg "(disabled, see /etc/default/${NAME})"
        else    
            start-stop-daemon --start \
            --chuid $USER \
            $START_STOP_OPTIONS \
            --exec $DAEMON -- $OPTIONS
        fi
    }
    
    case "$1" in
        start)
            log_daemon_msg "Starting bittorrent daemon" "$NAME"
            start_daemon
            log_end_msg 0
            ;;
        stop)
            log_daemon_msg "Stopping bittorrent daemon" "$NAME"
            start-stop-daemon --stop --quiet \
                --exec $DAEMON --retry $STOP_TIMEOUT \
                --oknodo
            log_end_msg 0
            ;;
        reload)
            log_daemon_msg "Reloading bittorrent daemon" "$NAME"
            start-stop-daemon --stop --quiet \
                --exec $DAEMON \
                --oknodo --signal 1
            log_end_msg 0
            ;;
        restart|force-reload)
            log_daemon_msg "Restarting bittorrent daemon" "$NAME"
            start-stop-daemon --stop --quiet \
                --exec $DAEMON --retry $STOP_TIMEOUT \
                --oknodo
            start_daemon
            log_end_msg 0
            ;;
        status)
            status_of_proc "$DAEMON" "$NAME" && exit 0 || exit $?
            ;;
        *)
            echo "Usage: /etc/init.d/$NAME {start|stop|reload|force-reload|restart|status}"
            exit 2
            ;;
    esac
    
    exit 0

```

---

### Post by ian-weisser on 2014-01-02
Perhaps you are trying to modify the wrong file.

Ubuntu uses Upstart.
Transmission's Upstart job is at /etc/init/transmission-daemon.conf. Try adding the logging flag there.
The /etc/init.d/transmission-daemon script may not be used by your system, but merely included for Debian sysvinit compatibility.

---

### Post by SpinUp on 2014-01-13
I've got transmission installed from the PPA, and I have the script under /etc/init.d/ and no upstart job under /etc/init/.  On my system, transmission-daemon has been logging to syslog by default.  Have you tried:

>  grep -i transmission /var/log/syslog

---

