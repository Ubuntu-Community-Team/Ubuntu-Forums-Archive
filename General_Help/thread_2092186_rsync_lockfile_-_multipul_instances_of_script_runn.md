---
title: "rsync lockfile - multipul instances of script running"
date: 2012-12-07
forum: General Help
---

### Post by kpholmes on 2012-12-07
i have a rsync script setup to check for new files on a remote machine every 5 minutes. it these are large files so it takes longer then 5 minutes to transfer. 

what i would like to have is rsync check every 5 minutes and download new files, but if another instance of that script is running then to close/quit.

from what ive read on the internet is to make a lock file, and ive tried a couple so far with no success:

```

           LOCK=<pathrun in inn.conf>/LOCK.send
           trap 'rm -f ${LOCK} ; exit 1' 1 2 3 15
           if shlock -p $$ -f ${LOCK} ; then
               # Do appropriate work.
           else
               echo "Locked by `cat ${LOCK}`"
           fi
```

```
PIDFILE=/var/run/myscript.pid

if [ -e "$PIDFILE" ] ; then
    # our pidfile exists, let's make sure the process is still running though
    PID=`/bin/cat "$PIDFILE"`
    if /bin/kill -0 "$PID" > /dev/null 2>&1 ; then
        # indeed it is, i'm outta here!
        /bin/echo 'The script is still running, forget it!'
        exit 0
    fi
 fi

 # create or update the pidfile
 /bin/echo "$$" > $PIDFILE

 ... do stuff ...

 /bin/rm -f "$PIDFILE"
```

i did see something about giving the script a reserved [pid] and having some code in the rsync script check and see if a process like that is already running.

another one ive also seen and tried was creating a lockfile in /tmp but that requires root and i dont want to run this script as root.

thanks,
any help would be appreciated

---

### Post by kpholmes on 2012-12-07
fixed it, :lolflag:

this script here did the trick actually. i just had to put the .pid file where the user had proper permissions ](*,)


```
PIDFILE=/var/run/myscript.pid

if [ -e "$PIDFILE" ] ; then
    # our pidfile exists, let's make sure the process is still running though
    PID=`/bin/cat "$PIDFILE"`
    if /bin/kill -0 "$PID" > /dev/null 2>&1 ; then
        # indeed it is, i'm outta here!
        /bin/echo 'The script is still running, forget it!'
        exit 0
    fi
 fi

 # create or update the pidfile
 /bin/echo "$$" > $PIDFILE

 ... do stuff ...

 /bin/rm -f "$PIDFILE"
```

---

