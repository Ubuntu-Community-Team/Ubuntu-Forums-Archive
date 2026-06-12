---
title: "Need help editing runtime script"
date: 2008-05-02
forum: General Help
---

### Post by Beacon11 on 2008-05-02
Hello all. I recently installed knockd on this Kubuntu laptop (don't worry, it's not a server-- in my situation, there are no security implications of using port knocking). However, the default package installs a runtime script that default to using eth0 (my wired). I use eth1 (wireless) more often than eth0, so I was going to change the script. However, I have an even better idea-- unfortunately, I've never done this before so I could use some help.

I want to do this: if eth0 is active, then use eth0. Otherwise, use eth1. If eth1 isn't active, fail.

It'd truly be ideal if I could somehow make it so that knockd listens over whatever interface is active, and can switch to wireless immediately when I unplug my wired. However, in my mind, for a startup script, this isn't possible. I can live with rebooting if I remove the cable from eth0 if I must. Anyway, here's the script as it is now:

```

#! /bin/sh

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/knockd
DEFAULT=/etc/default/knockd
NAME=knockd
DESC="Port-knock daemon"
OPTIONS=" -d"

umask 0037

test -f $DAEMON || exit 0

set -e

if [ -f $DEFAULT ]; then
    . $DEFAULT
fi

[ "$KNOCKD_OPTS" ] && OPTIONS="$OPTIONS $KNOCKD_OPTS"

case "$1" in
  start)
        if [ $START_KNOCKD -ne 1 ]; then
                echo "Not starting knockd. To enable it edit $DEFAULT"
                exit 0
        fi
        echo -n "Starting $DESC: "
        start-stop-daemon --start --oknodo --quiet --exec $DAEMON -- $OPTIONS
        echo "$NAME."
        ;;
  stop)
        echo -n "Stopping $DESC: "
        start-stop-daemon --stop --oknodo --quiet --exec $DAEMON
        echo "$NAME."
        ;;
  restart|reload|force-reload)
        echo -n "Restarting $DESC: "
        start-stop-daemon --stop --oknodo --quiet --exec $DAEMON
        if [ $START_KNOCKD -ne 1 ]; then
                echo "Not starting knockd. To enable it edit $DEFAULT"
                exit 0
        fi
        sleep 1
        start-stop-daemon --start --oknodo --quiet --exec $DAEMON -- $OPTIONS
        echo "$NAME."
        ;;
  *)
        echo "Usage: $0 {start|stop|restart|reload|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

As you can see... nothing in there talks about eth0, but I can pass it in the $OPTIONS.

Can someone help me accomplish this? As I said, I've never done this before and could use some help. Thank you! :)

---

