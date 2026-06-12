---
title: "/etc/init.d script with 2 instances of start-stop-daemon doesn't work"
date: 2013-06-12
forum: General Help
---

### Post by kalehrl on 2013-06-12
Hi
I'm having trouble with a script in which there are 2 instances of start-stop-daemon in both start and stop sections.
The script:
```
#!/bin/bash

SBOX=/usr/local/bin/sbox
CCCAM=/usr/local/bin/cccam

case "$1" in
start)
    exec start-stop-daemon -S -x $SBOX -- -c /var/etc/sbox/
    exec start-stop-daemon -S -x $CCCAM
    ;;
stop)
    exec start-stop-daemon -K -R 2 -x $SBOX
    exec start-stop-daemon -K -R 2 -x $CCCAM
    ;;
restart)
    $0 stop
    sleep 1
    $0 start
    ;;
*)
    echo "Usage: $0 start|stop|restart"
    exit 1
    ;;
esac
exit 0
```
The problem with this script is that it doesn't start or stop the second daemon - /usr/local/bin/cccam.
It only starts and stops the first daemon - /usr/local/bin/sbox.
Does anyone know why it is the case?
Thank you

---

