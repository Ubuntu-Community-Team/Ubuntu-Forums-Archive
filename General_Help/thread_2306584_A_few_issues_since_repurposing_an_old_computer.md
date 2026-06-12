---
title: "A few issues since repurposing an old computer"
date: 2015-12-16
forum: General Help
---

### Post by sidcypher-b on 2015-12-16
I had been running Desktop Ubuntu 14 on the machine in question until recently when I built a new computer.

I decided to reformat the old machine and install Server Ubuntu 14.04.3 to run it headless.

Still pretty new to running everything through a terminal window so I don't understand everything quite yet. I didn't realize how handy the Gui can be nor how powerful the terminal can be..

Having a few issues since the reinstall.

proftpd, and transmission-daemon

both have to be manually restarted after a reboot
otherwise FTP client refuses connection
and transmission-daemon remote doesn't work

```
Results of service --status-all right after boot up
james@Beast:~$ service --status-all
 [ + ]  acpid
 [ - ]  apparmor
 [ ? ]  apport
 [ + ]  atd
 [ ? ]  console-setup
 [ + ]  cron
 [ - ]  dbus
 [ ? ]  dns-clean
 [ + ]  friendly-recovery
 [ - ]  grub-common
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ ? ]  kmod
 [ ? ]  networking
 [ ? ]  ondemand
 [ ? ]  pppd-dns
 [ - ]  procps
 [ + ]  proftpd
 [ ? ]  rc.local
 [ + ]  resolvconf
 [ - ]  rsync
 [ + ]  rsyslog
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ - ]  sphinxsearch
 [ - ]  ssh
 [ - ]  sudo
 [ + ]  transmission-daemon
 [ - ]  udev
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  webmin
 [ - ]  x11-common

and more right after reboot

james@Beast:~$ sudo service proftpd status
[sudo] password for james:
ProFTPD is started in standalone mode, currently running.
james@Beast:~$ sudo service transmission-daemon status
transmission-daemon start/running, process 506


```

They both always show a [+]
Tried to paste the FileZilla log showing connection refused.. but it actually worked this time.. 
Transmission web interface shows page can not be displaced
and Windows Transmission Remote GUI says Connection Refused
```
james@Beast:~$ sudo service transmission-daemon start
start: Job is already running: transmission-daemon
james@Beast:~$ sudo service transmission-daemon restart
transmission-daemon stop/waiting
transmission-daemon start/running, process 1391

```
is required to get the web interface/remote working

I do not know if/where a boot log file would be, but if you need it just let me know where it is and I will paste it.

No idea how to fix those, but I am guessing they would be under one category..

This being under a different category. The other problem I am having is mounting a NAS at boot

It is currently being mounted to **/media/nastysid **using the below in fstab, which I found the basics of that via Google ```
//192.168.1.102/share /media/nastysid cifs username=guest,password=,iocharset=utf8 0 0

```

I can "cp" from the NAS to the Ubuntu machine but not "cp" to the NAS from the Ubuntu machine unless I use "sudo," which is causing problems with some scripts to copy my downloads to the NAS

```
james@Beast:~$ cp SM-server.sh /media/nastysid/SM-server.sh
cp: cannot create regular file ‘/media/nastysid/SM-server.sh’: Permission denied
james@Beast:~$ sudo cp SM-server.sh /media/nastysid/SM-server.sh
james@Beast:~$ cd /media/nastysid
james@Beast:/media/nastysid$ cp SM-server.sh /home/james/server.sh
james@Beast:/media/nastysid$


```
Random bonus question

I use the computer to host a Star Made server now for a myself and a few buddies..

Is there a way to set it up where upon boot up it would automatically create a new screen and execute the server script on the new virtual screen? Like...```
screen -R starmade
./SM-server.sh
``` and at shutdown send the Starmade server shutdown command ```
/shutdown 10
```to that screen and pause allowing time for it to shutdown, say 20-30 seconds, then resume system shutdown/reboot?

also for ease of use with scripts everything is running as my username instead of the defaults like a proftpd user, transmission-daemon user, etc.. as I found out that can also cause issues with scripts because of owning the files.

I tried to provide as much information as possible, if I have left anything out just let me know what (and the command) and I will post it as quick as I can.

Thanks!

---

### Post by TheFu on 2015-12-18
Welcome to the forums!
BTW, it is best to ask 1 question per thread. Use a good thread title and put the question into the correct sub-sub-sub-forum to get help from those experts.

I've never trusted any "service" commands.  They just call the scripts in /etc/init.d/.  I much prefer just to call the scripts directly.  If you want to know whether something is running or not, check the process table using **ps** + **grep**.  Something like **ps -eaf|grep apache** - don't trust "service status" or chkconfig tools. They only work for a subset of commands.

If you want something to startup as a daemon after reboot, use **update-rc.d** to control which runlevel it starts under. Runlevels are basic admin knowledge.

I stopped using FTP in the 1990s. Why?  [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)  I used to say "NEVER use plain FTP", but there are good reasons to use it - like when you want anyone, anywhere, in the world, to have complete access to your system, not just to the FTP areas.  FTP isn't firewall friendly and sftp is much easier and more secure for authenticated accounts. HTTP can be used for un-authenticated file transfers.  Why use plain FTP?  Ok - I'm a hater of FTP. I can admit it. ;)

For sharing storage, NFS is king.  File permissions are the same - local or over NFS. No confusion, just map the userids/groupids to match on all the systems. You can mount NFS storage anywhere you like.  CIFS is 2nd class storage protocol, IMHO. Only useful for Windows clients.  OSX, Linux, Unix all should use NFS instead ... on the LAN. Over a WAN connection, sshfs or sftp are best.  I will admit to using CIFS on the LAN for Windows clients. That same storage is available via NFS for Unix clients.

Don't know anything about transmission.

Also, as systemd takes over more and more of Ubuntu, the methods to control daemons will change drastically.  I'm still on 14.04 and 12.04, so haven't had to deal with systemd much.

Hope this helps in some way.

---

### Post by ian-weisser on 2015-12-19
> **sidcypher-b said:**
> proftpd, and transmission-daemon both have to be manually restarted after a reboot
otherwise FTP client refuses connection
and transmission-daemon remote doesn't work

Perhaps they are being started before the network is available?

Locate the init.d script or Upstart Job that starts each malfunctioning service.
Show them to us.

---

### Post by sidcypher-b on 2015-12-19
TheFu

I will read up on the update-rc.d, though from what I have briefly seen it looks pretty confusing..

I am using sftp only within the local network because it was annoying me having to sudo cp commands, since because of that my script isn't working.. I am ftp'ing the downloads to another machine (renaming and sorting) before copying them to the NAS..

ian-weisser

Here are the init.d scripts, I don't know where the upstart jobs would be located they are pretty much the default of how it was setup

proftpd
```
#!/bin/sh


### BEGIN INIT INFO
# Provides:          proftpd
# Required-Start:    $remote_fs $syslog $local_fs $network
# Required-Stop:     $remote_fs $syslog $local_fs $network
# Should-Start:      $named
# Should-Stop:       $named
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts ProFTPD daemon
# Description:       This script runs the FTP service offered
#                    by the ProFTPD daemon
### END INIT INFO


# Start the proftpd FTP daemon.


PATH=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/sbin/proftpd
NAME=proftpd


# Defaults
RUN="no"
OPTIONS=""
CONFIG_FILE=/etc/proftpd/proftpd.conf


PIDFILE=`grep -i 'pidfile' $CONFIG_FILE|sed -e 's/pidfile[\t ]\+//i'`
if [ "x$PIDFILE" = "x" ];
then
        PIDFILE=/var/run/proftpd.pid
fi


# Read config (will override defaults)
[ -r /etc/default/proftpd ] && . /etc/default/proftpd


trap "" 1
trap "" 15


test -f $DAEMON || exit 0


. /lib/lsb/init-functions


#
# Servertype could be inetd|standalone|none.
# In all cases check against inetd and xinetd support.
#
if ! egrep -qi "^[[:space:]]*ServerType.*standalone" $CONFIG_FILE
then
        if egrep -qi "server[[:space:]]*=[[:space:]]*/usr/sbin/(in\.)?proftpd" /etc/xinetd.conf 2>/dev/null || \
           egrep -qi "server[[:space:]]*=[[:space:]]*/usr/sbin/(in\.)?proftpd" /etc/xinetd.d/* 2>/dev/null || \
           egrep -qi "^ftp.*/usr/sbin/(in\.)?proftpd" /etc/inetd.d/* 2>/dev/null || \
           egrep -qi "^ftp.*/usr/sbin/(in\.)?proftpd" /etc/inetd.conf 2>/dev/null
        then
                RUN="no"
                INETD="yes"
        else
                if ! egrep -qi "^[[:space:]]*ServerType.*inetd" $CONFIG_FILE
                then
                RUN="yes"
                        INETD="no"
                else
                        RUN="no"
                        INETD="no"
                fi
        fi
fi


# /var/run could be on a tmpfs


[ ! -d /var/run/proftpd ] && mkdir /var/run/proftpd


inetd_check()
{
        if [ ! -x /usr/sbin/inetd -a ! -x /usr/sbin/xinetd -a \
             ! -x /usr/sbin/inetutils-inetd ]; then
                echo "Neither inetd nor xinetd appears installed: check your configuration."
        fi
}


start()
{
    log_daemon_msg "Starting ftp server" "$NAME"


    start-stop-daemon --start --quiet --pidfile "$PIDFILE" --oknodo --exec $DAEMON -- -c $CONFIG_FILE $OPTIONS
    if [ $? != 0 ]; then
        log_end_msg 1
        exit 1
    else
        log_end_msg 0
    fi
}


signal()
{


    if [ "$1" = "stop" ]; then
                SIGNAL="TERM"
        log_daemon_msg "Stopping ftp server" "$NAME"
    else
        if [ "$1" = "reload" ]; then
            SIGNAL="HUP"
        log_daemon_msg "Reloading ftp server" "$NAME"
        else
            echo "ERR: wrong parameter given to signal()"
            exit 1
        fi
    fi
    if [ -f "$PIDFILE" ]; then
        start-stop-daemon --stop --signal $SIGNAL --quiet --pidfile "$PIDFILE"
         if [ $? = 0 ]; then
                log_end_msg 0
        else
                SIGNAL="KILL"
                start-stop-daemon --stop --signal $SIGNAL --quiet --pidfile "$PIDFILE" --retry=TERM/10/KILL/5
                if [ $? != 0 ]; then
                        log_end_msg 1
                        [ $2 != 0 ] || exit 0
                else
                        log_end_msg 0
                fi
        fi
        if [ "$SIGNAL" = "KILL" ]; then
                rm -f "$PIDFILE"
        fi
    else
        log_end_msg 0
    fi
}


case "$1" in
    start)
        if [ "x$RUN" = "xyes" ] ; then
            start
        else
            if [ "x$INETD" = "xyes" ] ; then
                echo "ProFTPD is started from inetd/xinetd."
                inetd_check
            else
                echo "ProFTPD warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration."
            fi
        fi
        ;;


    force-start)
        if [ "x$INETD" = "xyes" ] ; then
            echo "Warning: ProFTPD is started from inetd/xinetd (trying to start anyway)."
                inetd_check
        fi
        start
        ;;


    stop)
        if [ "x$RUN" = "xyes" ] ; then
            signal stop 0
        else
            if [ "x$INETD" = "xyes" ] ; then
                echo "ProFTPD is started from inetd/xinetd."
                inetd_check
            else
                echo "ProFTPD warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration."
            fi
        fi
        ;;


    force-stop)
        if [ "x$INETD" = "xyes" ] ; then
            echo "Warning: ProFTPD is started from inetd/xinetd (trying to kill anyway)."
                inetd_check
        fi
        signal stop 0
        ;;


    reload)
        signal reload 0
        ;;


    force-reload|restart)
        if [ "x$RUN" = "xyes" ] ; then
            signal stop 1
            start
        else
            if [ "x$INETD" = "xyes" ] ; then
                echo "ProFTPD is started from inetd/xinetd."
                inetd_check
            else
                echo "ProFTPD warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration."
            fi
        fi
        ;;


    status)
        if [ "x$INETD" = "xyes" ] ; then
            echo "ProFTPD is started from inetd/xinetd."
                inetd_check
                exit 0
        else
            if [ -f "$PIDFILE" ]; then
                pid=$(cat $PIDFILE)
            else
                pid="x"
            fi
            if [ `pidof proftpd|grep "$pid"|wc -l` -ne 0 ] ; then
                echo "ProFTPD is started in standalone mode, currently running."
                        exit 0
            else
                echo "ProFTPD is started in standalone mode, currently not running."
                        exit 3
            fi
        fi
        ;;


    check-config)
        $DAEMON -t >/dev/null && echo "ProFTPD configuration OK" && exit 0
        exit 1
        ;;


    *)
        echo "Usage: /etc/init.d/$NAME {start|status|force-start|stop|force-stop|reload|restart|force-reload|check-config}"
        exit 1
        ;;
esac


exit 0


```

Transmission-daemon

```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          transmission-daemon
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:     $local_fs $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start or stop the transmission-daemon.
# Description:       Enable service provided by transmission-daemon.
### END INIT INFO


NAME=transmission-daemon
DAEMON=/usr/bin/$NAME
USER=james
STOP_TIMEOUT=30


export PATH="${PATH:+$PATH:}/sbin"


[ -x $DAEMON ] || exit 0


[ -e /etc/default/$NAME ] && . /etc/default/$NAME


. /lib/lsb/init-functions


start_daemon () {
    if [ $ENABLE_DAEMON != 1 ]; then
        log_progress_msg "(disabled)"
                log_end_msg 255 || true
    else
        start-stop-daemon --start \
        --chuid $USER \
                $START_STOP_OPTIONS \
        --exec $DAEMON -- $OPTIONS || log_end_msg $?
                log_end_msg 0
    fi
}


case "$1" in
    start)
        log_daemon_msg "Starting bittorrent daemon" "$NAME"
        start_daemon
        ;;
    stop)
        log_daemon_msg "Stopping bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON --retry $STOP_TIMEOUT \
            --oknodo || log_end_msg $?
        log_end_msg 0
        ;;
    reload)
        log_daemon_msg "Reloading bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON \
            --oknodo --signal 1 || log_end_msg $?
        log_end_msg 0
        ;;
    restart|force-reload)
        log_daemon_msg "Restarting bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON --retry $STOP_TIMEOUT \
            --oknodo || log_end_msg $?
        start_daemon
        ;;
    status)
        status_of_proc "$DAEMON" "$NAME" && exit 0 || exit $?
        ;;
    *)
        log_action_msg "Usage: /etc/init.d/$NAME {start|stop|reload|force-reload|restart|status}" || true
        exit 2
        ;;
esac


exit 0


```

---

### Post by TheFu on 2015-12-19
update-rc.d is how ubuntu manages which services (daemons) are started and stopped based on the runlevel. Runlevel management is a basic Unix admin thing.  I'd guess that debian does this too ... at least for now, until systemd takes over and drops the idea of "runlevel" that has been the heart of Unix startup since ... 1970.

---

### Post by ian-weisser on 2015-12-19
Perhaps $network is firing too early...or not at all, or perhaps in response to the wrong signal.
On a 14.04 system, init is Upstart (not sysvinit), which signals 'network-up' instead. If you look in /etc/init, you should see all the networking Upstart jobs.

Test: 

Create a script in init.d that simply depends upon $network.
Have that script log to /var/log/syslog when its activated.
Reboot.
Check /var/log/syslog to compare when $network is being signalled vs. when the network interface actually comes up.

---

