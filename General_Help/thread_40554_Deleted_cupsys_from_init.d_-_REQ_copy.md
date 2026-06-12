---
title: "Deleted cupsys from init.d - REQ: copy"
date: 2005-06-09
forum: General Help
---

### Post by pem725 on 2005-06-09
Greetings,

I was hoping someone could post the original cupsys file from /etc/init.d.  I deleted it thinking that apt-get would stick a new one back in its place.  No such luch so I am without cups.  BTW, I am struggling to get cups to work.  I have the folllowing strange error in my log file:

cups cannot assign requested address

So, if some kind soul could post the cupsys file I would be extremely grateful.  Thanks in advance.

Cheers,

Patrick

---

### Post by desdinova on 2005-06-09
cat /etc/init.d/cupsys
#! /bin/sh
#
# cupsys        example file to build /etc/init.d/ scripts.
#               This file should be used to construct scripts for /etc/init.d.
#
#               Written by Miquel van Smoorenburg <miquels@cistron.nl>.
#               Modified for Debian GNU/Linux
#               by Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
# Version:      @(#)skeleton  1.8  03-Mar-1998  [email]miquels@cistron.nl[/email]
#
# This file was automatically customized by dh-make on Sun,  3 Oct 1999 20:58:02 -0500

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/cupsd
NAME=cupsd
DESC="Common Unix Printing System"

test -f $DAEMON || exit 0

set -e

# Get the timezone set.
if [ -e /etc/timezone ]; then
    TZ=`cat /etc/timezone`
    export TZ
fi

. /lib/lsb/init-functions

case "$1" in
  start)
        log_begin_msg "Starting $DESC: $NAME"

        # allow lpadmin users to add printer drivers
        chown root:lpadmin /usr/share/cups/model 2>/dev/null || true
        chmod 3775 /usr/share/cups/model 2>/dev/null || true

        start-stop-daemon --start --quiet --background --exec $DAEMON -- -F
        log_end_msg $?
        ;;
  stop)
        log_begin_msg "Stopping $DESC: $NAME"
        start-stop-daemon --stop --quiet --retry TERM/10 --oknodo --exec $DAEMON
        log_end_msg $?
        ;;
  restart|force-reload)
        log_begin_msg "Restarting $DESC: $NAME"
        if start-stop-daemon --stop --quiet --retry TERM/10 --oknodo --exec $DAEMON; then
                start-stop-daemon --start --quiet --exec $DAEMON
                log_end_msg $?
        else
                log_end_msg $?
        fi
        ;;
  *)
        N=/etc/init.d/$NAME
        # echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
        log_success_msg "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

---

### Post by pem725 on 2005-06-09
Thanks mate.

---

