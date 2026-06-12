---
title: "Ubuntu init script fails during boot but successfully starts from a desktop session"
date: 2014-06-24
forum: General Help
---

### Post by akimb0 on 2014-06-24
Hello,

i have a problem with an init.d script i used on CentOS and Ubuntu 12.04 before and im now trying to use this script also in Ubuntu 14.04 (fresh install). CentOS, 12.04 and now 14.04 were all 64bit versions.
I placed my script (like i did it on 12.04 before) to /etc/init.d

```
/etc/init.d/script_test
```

 and updated rc.d


  ```
sudo update-rc.d /etc/init.d/script_test defaults 20 20
```

This is the script that works on CentOS and also on Ubuntu 12.04
```
#!/bin/bash
#
# chkconfig: 2345 84 16     
# processname: CMserve
# pidfile: /var/run/CMserve.pid
# config: /etc/sysconfig/CMserve

# source function library
. /etc/init.d/functions

DEBUG=1
RETVAL=0

start() {
    echo -n $"Starting CMserve service: "

    if [ ${DEBUG} -eq 1 ]
    then
        echo "[debugging enabled]"
        ulimit -c unlimited;
        cd /usr/local/CMserve;
    fi
    /usr/local/CMserve/CMserve >/var/log/CMserve 2>&1 &
    RETVAL=$?
    echo
    [ $RETVAL -eq 0 ] && touch /var/lock/CMserve
}

stop() {
    echo -n $"Shutting down CMserve service: "
    pkill CMserve
    RETVAL=$?

    echo
    [ $RETVAL -eq 0 ] && rm -f /var/lock/CMserve
}

case "$1" in
  start)
    start
    ;;
  stop)
    stop
    ;;
  restart|reload)
    stop
    start
    RETVAL=$?
    ;;
  condrestart)
    if [ -f /var/lock/CMserve ]; then
        stop
        start
        RETVAL=$?
    fi
    ;;
  status)
    status CMserve
    RETVAL=$?
    ;;
  *)
    echo $"Usage: $0 {start|stop|restart|condrestart|status}"
    exit 1
esac

exit $RETVAL
```

The problem is that the script fails with SIGSEGV on libc-2.19 during bootup but i can manually start/stop/restart this script from a desktop session and the CMserve binary damonize fine without an error. 

This is what i found in the kernel.log
```

kernel: [   92.061834] traps: CMserve[2038] general protection ip:7f2b37c28f44 sp:7f2b369b1338 error:0 in libc-2.19.so[7f2b37b20000+1bc000]
kernel: [   92.061839]  in libc-2.19.so[7f3edf546000+1bc000]

```

I have absolutely no clue why this works well from a desktop session on the one hand and fails during bootup on the other!?
Is there anything i could dump here during bootup to get more informations about this issue? Do i need to downgrade libc?
Any help would be much appreciated.

I have also asked this on AskUbuntu [http://askubuntu.com/questions/486128/ubuntu-14-04-etc-init-d-script-got-sigsegv-in-pthread-mutex-lock-during-boot-bu](http://askubuntu.com/questions/486128/ubuntu-14-04-etc-init-d-script-got-sigsegv-in-pthread-mutex-lock-during-boot-bu)

---

### Post by akimb0 on 2014-06-24
Oh and i forgot to state that i linked /lib/lsb/init-functions to /etc/init.d/functions to avoid function errors

---

