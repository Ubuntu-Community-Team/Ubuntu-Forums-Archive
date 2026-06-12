---
title: "output of init.d scripts"
date: 2015-04-10
forum: General Help
---

### Post by rkevinburton on 2015-04-10
I see various lines such as echo "I'm here" in the init.d scripts. Where does this output go? Like I have a script that works just fine. A portion of the script looks like:
case "$1" in
    start)
        if [ -f $PIDFILE ]
        then
                echo "$PIDFILE exists, process is already running or crashed"
        else
                echo "Starting Redis server $REDISPORT ..."
                $EXEC $CONF
        fi
        ;;
    stop)
        if [ ! -f $PIDFILE ]
        then
                echo "$PIDFILE does not exist, process is not running"
        else
                PID=$(cat $PIDFILE)


The service is started on boot. Where would I look to see the 'echo' output?

---

### Post by ian-weisser on 2015-04-13
Nowhere. Those lines were for testing the logic.

Root runs those scripts. Root doesn't have a display for output, so the output is discarded.
A user running those scripts -after changing the file ownership or permissions-  would get output on their assigned display (Terminal)...but the start/stop/restart actions would fail because they are not root.

Generally, when root produces output for a human to see, it writes to the appropriate logfile instead of a display, or sends an e-mail.

---

