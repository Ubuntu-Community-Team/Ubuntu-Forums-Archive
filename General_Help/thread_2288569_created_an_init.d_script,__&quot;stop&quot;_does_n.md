---
title: "created an init.d script,  &quot;stop&quot; does not work"
date: 2015-07-28
forum: General Help
---

### Post by ubu_Leno on 2015-07-28
Hello everybody

I have a small test daemon and an init.d script for it.  The daemon works as expected and is started by the script but the init script does not work   */etc/init.d/myScriptd stop*  looks to work but the daemon still runs.

The init script works to start the daemon but the stop option does not work.

Below is the init.d script.  Is there a mistake I am making?

For reference, here is output of ps aux for the daemon

```

myScript      7541  0.0  0.8 226336 34652 ?        Ss   11:16   1:22 myScriptd (master)
myScript      8341  1.2  1.8 325177 72252 ?        S    12:04   0:05 myScriptd (xxD-avail)
myScript      8360  0.4  1.7 309798 69076 ?        S    12:06   0:01 myScriptd (xxF-avail)

```

I have tried the init.d script with the stop section calling *--name $PNAME*  and *--name $PNAMEFULL* neither work

```

#! /bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin
NAME=myScriptd
SNAME=myScriptd
DAEMON=/usr/sbin/myScriptd
DESC="myScript Mail Filter Daemon"
PIDFILE="/var/run/myScript/$NAME.pid"
PNAME="myScriptd"
PNAMEFULL="myScriptd\ \(master\)"

export TMPDIR=/tmp

# Defaults - don't touch, edit /etc/default/myScriptd
ENABLED=0
OPTIONS=""
NICE=
##########

test -f /etc/default/myScriptd && . /etc/default/myScriptd

if [ "$ENABLED" = "0" ]; then
    echo "$DESC: disabled, see /etc/default/myScriptd"
    exit 0
fi

test -f $DAEMON || exit 0

set -e

case "$1" in
  start)
    echo -n "Starting $DESC: "
    start-stop-daemon --start --pidfile $PIDFILE --name $PNAME \
        $NICE --oknodo --startas $DAEMON -- $OPTIONS $DOPTIONS
    echo "$NAME."
    ;;

  stop)
    echo -n "Stopping $DESC: "
    start-stop-daemon --stop --pidfile $PIDFILE --name $PNAME --oknodo
    rm $PIDFILE
    echo "$NAME."
    ;;

  reload|force-reload)
    echo -n "Reloading $DESC: "
    start-stop-daemon --stop --pidfile $PIDFILE --signal HUP --name $PNAME
    echo "$NAME."
    ;;

  restart)
    echo -n "Restarting $DESC: "
    start-stop-daemon --stop --pidfile $PIDFILE --name $PNAME \
        --retry 5 --oknodo
    start-stop-daemon --start --pidfile $PIDFILE --name $PNAME \
        $NICE --oknodo --startas $DAEMON -- $OPTIONS $DOPTIONS

    echo "$NAME."
    ;;

  *)
    N=/etc/init.d/$SNAME
    echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
    exit 1
    ;;
esac

exit 0

```

---

### Post by dino99 on 2015-07-28
are you booted with upstart or systemd ?

---

### Post by ubu_Leno on 2015-07-28
ah upstart I think?  How do I tell, it's Ubuntu Server 12.04

---

### Post by ubu_Leno on 2015-10-22
would anyone have suggestions on getting this working?

---

