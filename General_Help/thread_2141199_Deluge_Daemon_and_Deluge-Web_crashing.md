---
title: "Deluge Daemon and Deluge-Web crashing"
date: 2013-05-01
forum: General Help
---

### Post by zaphod777 on 2013-05-01
I have deluged daemon and deluge-web running on my server that auto starts and connects the web-ui to the daemon so I can use things like transdroid. The problem is that the daemon, web ui, or both keep crashing. I can't figure out what is happening, sometimes they will run for days or weeks and other times a few hours to a day. 

I am running:
deluged: 1.3.6
deluge-web: 1.3.6
libtorrent: 0.15.10.0

The only thing I can see in the Deluged and Web-UI logs are:
```
hal:/var/log/deluge/daemon$ cat ../web/warning.log
[ERROR   ] 13:22:44 config:371 
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/deluge/config.py", line 369, in load
    self.__config.update(pickle.loads(data))
EOFError
[WARNING ] 13:22:44 config:372 Unable to load config file: /home/xbmc/.config/deluge/hostlist.conf.1.2
```


here is the deluge-daemon in my /etc/init.d
```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          deluge-daemon
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      $network
# Should-Stop:       $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Daemonized version of deluge and webui.
# Description:       Starts the deluge daemon with the user specified in
#                    /etc/default/deluge-daemon.
### END INIT INFO

# Author: Adolfo R. Brandes 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Deluge Daemon"
NAME1="deluged"
NAME2="deluge"
DAEMON1=/usr/bin/deluged
DAEMON1_ARGS="-d -L warning -l /var/log/deluge/daemon/warning.log"             # Consult `man deluged` for more options
DAEMON2=/usr/bin/deluge-web
DAEMON2_ARGS="-L warning -l /var/log/deluge/web/warning.log"               # Consult `man deluge-web` for more options
PIDFILE1=/var/run/$NAME1.pid
PIDFILE2=/var/run/$NAME2.pid
UMASK=022                     # Change this to 0 if running deluged as its own user
PKGNAME=deluge-daemon
SCRIPTNAME=/etc/init.d/$PKGNAME

# Exit if the package is not installed
[ -x "$DAEMON1" -a -x "$DAEMON2" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$PKGNAME ] && . /etc/default/$PKGNAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

if [ -z "$RUN_AT_STARTUP" -o "$RUN_AT_STARTUP" != "YES" ]
then
   log_warning_msg "Not starting $PKGNAME, edit /etc/default/$PKGNAME to start it."
   exit 0
fi

if [ -z "$DELUGED_USER" ]
then
    log_warning_msg "Not starting $PKGNAME, DELUGED_USER not set in /etc/default/$PKGNAME."
    exit 0
fi

#
# Function that starts the daemon/service
#
do_start()
{
   # Return
   #   0 if daemon has been started
   #   1 if daemon was already running
   #   2 if daemon could not be started
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER --umask $UMASK --test > /dev/null
   RETVAL1="$?"
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER --umask $UMASK --test > /dev/null
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 1

   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --make-pidfile --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER --umask $UMASK -- $DAEMON1_ARGS
   RETVAL1="$?"
        sleep 2
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --make-pidfile --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER --umask $UMASK -- $DAEMON2_ARGS
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 2
}

#
# Function that stops the daemon/service
#
do_stop()
{
   # Return
   #   0 if daemon has been stopped
   #   1 if daemon was already stopped
   #   2 if daemon could not be stopped
   #   other if a failure occurred

   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE2
   RETVAL2="$?"
   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE1
   RETVAL1="$?"
   [ "$RETVAL1" = "2" -o "$RETVAL2" = "2" ] && return 2

   rm -f $PIDFILE1 $PIDFILE2

   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] && return 0 || return 1
}

case "$1" in
  start)
   [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME1"
   do_start
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  stop)
   [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME1"
   do_stop
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  restart|force-reload)
   log_daemon_msg "Restarting $DESC" "$NAME1"
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
   echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
   exit 3
   ;;
esac

:
```

---

### Post by zaphod777 on 2013-05-27
OK, it isn't exactly a solution but I created a script and scheduled a cronjob to check if deluged is running every 1 min and if not restart the service. &#65279;It then appends the date and time to a log file so you can see how often it is crashing. 

su
mkdir /root/Scripts
nano /root/Scripts/make-run.sh


```
#!/bin/bash
#make-run.sh
#make sure deluge is running

export DISPLAY=:0 #needed if you are running a simple gui app.

process=deluged
makerun="service deluge-daemon restart"

if ps ax | grep -v grep | grep $process > /dev/null
        then
                exit
        else
        $makerun &
	
echo "Date: " $(date) >> /root/Scripts/deluged.log
        fi
exit

```
chmod +x /root/Scripts/make-run.sh
crontab -e
```

* * * * * /root/Scripts/make-run.sh

```

---

### Post by CromsDog on 2013-06-03
I just started running into this problem myself.  I haven't been able to track down the reason as to why yet.  Have you made any headway or are you still relying on the crontab to restart the service?


> **zaphod777 said:**
> OK, it isn't exactly a solution but I created a script and scheduled a cronjob to check if deluged is running every 1 min and if not restart the service. &#65279;It then appends the date and time to a log file so you can see how often it is crashing. 

su
mkdir /root/Scripts
nano /root/Scripts/make-run.sh


```
#!/bin/bash
#make-run.sh
#make sure deluge is running

export DISPLAY=:0 #needed if you are running a simple gui app.

process=deluged
makerun="service deluge-daemon restart"

if ps ax | grep -v grep | grep $process > /dev/null
        then
                exit
        else
        $makerun &
    
echo "Date: " $(date) >> /root/Scripts/deluged.log
        fi
exit

```
chmod +x /root/Scripts/make-run.sh
crontab -e
```

* * * * * /root/Scripts/make-run.sh

```

---

### Post by zaphod777 on 2013-06-17
I have a suspicion that it is a bug in libtorrent since I had the same problem with a few other torrent applications. For now I have just been using the cron job since it "fixes" it until I can find a real solution. It isn't ideal but at least I don't need to SSH in every time the dumb thing crashes.

---

### Post by sandyd on 2013-06-17
Have you tried running a stacktrace against deluge?
i.e. something like
```

strace -o /var/log/deluged.strace.log /usr/bin/deluged --do-not-daemonize -L debug -l /var/log/deluge/daemon.log

```
Now, when deluged crashes, you have a stacktrace sitting at /var/log/deluged.strace.log which you can probably report as a bug

---

### Post by HiImTye on 2013-06-17
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
I haven't noticed any crashes, but I'm still using 12.10 (with 1.3.5). try this guide:
[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

### Post by zaphod777 on 2013-06-17
> **sandyd said:**
> Have you tried running a stacktrace against deluge?
i.e. something like
```

strace -o /var/log/deluged.strace.log /usr/bin/deluged --do-not-daemonize -L debug -l /var/log/deluge/daemon.log

```
Now, when deluged crashes, you have a stacktrace sitting at /var/log/deluged.strace.log which you can probably report as a bug

How does that work with how I have the service running? Can I add that to the deluge-daemon I have running?

---

### Post by sandyd on 2013-06-17
> **zaphod777 said:**
> How does that work with how I have the service running? Can I add that to the deluge-daemon I have running?

[s]How are you starting it?

as a service, or using the deluged command.

If its as a service, I have no idea, since I dont see deluged in /etc/init.d or /etc/init.[/s]
Silly me not looking at post....

Firstly, stop deluged,
and run the above which will relaunch deluged with strace attached.

Also see HiImTye 's link above about reporting with apport, as strace only performs a stack trace, not a core dump

---

### Post by wHEEnrp on 2013-08-28
I had the same issue aswell how deluge seemed to either autoshutdown or crash either one.  But the script thing has worked for me I set it to check every 10 mins to put little strain on the pi (not sure how much strain those scheduled scripts put but anyway)

I also did what sandyd said how to use that command to write a log when the error occurs.  So my thing managed to crash and it created a log file but I have no idea how to read it as it is HUGE 500KBs of plain text.
So yea for those who are interested here you go.
[https://dl.dropboxusercontent.com/u/29472118/deluged.strace.log](https://dl.dropboxusercontent.com/u/29472118/deluged.strace.log)

---

### Post by dgray_from_dc on 2014-07-08
Did this issue ever get fully resolved?  I recently installed Deluge and configured flexget for automation.  Everything worked perfectly for several days, and suddenly the daemon started crashing every 10-15 seconds like the issue described in this thread.  Deluge has an older but similar thread on their forum [here]("http://forum.deluge-torrent.org/viewtopic.php?f=7&t=38423").  I installed the current version of deluge as described there, but it hasn't helped.  Anything new here?

---

### Post by sverker_wahlin on 2014-08-27
Thanks for this, it makes my deluge function! Doesn't remove the actual problem of it crashing, but hey, it works :)

love from Malmö

---

### Post by cardwell.bret on 2014-11-19
> **sandyd said:**
> Have you tried running a stacktrace against deluge?
i.e. something like
```

strace -o /var/log/deluged.strace.log /usr/bin/deluged --do-not-daemonize -L debug -l /var/log/deluge/daemon.log

```
Now, when deluged crashes, you have a stacktrace sitting at /var/log/deluged.strace.log which you can probably report as a bug

I know this thread is ancient (in internet terms) but I'm having a similar issue and have been unable to find a resolution.  My daemon dies after 20 - 30 minutes but starts right back with very little issue.  When I start the daemon with stacktrace,
```

strace -o /var/log/deluged.strace.log /usr/bin/deluged -L debug -l /var/log/deluge/daemon.log

```
 I immediately get 431 lines in the log.  Note that I removed "--do-not-daemonize" because it refused to run non-daemonized.

After the daemon crashed/stopped/ceased functioning, I checked the log again... still 431 lines and the first and last were identical to the pre-crash log.

Has anyone got an idea how to fix this or have a link to more good ideas?

Your daemon eternally,
   Wildboar/GreenWenonah/Blue150  I'm going skitzo with all my online identities.

---

