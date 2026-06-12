---
title: "Init.d scripting help?"
date: 2015-09-25
forum: General Help
---

### Post by leepe on 2015-09-25
hello everyone,
I'm writing an init.d script to start a program at boot and shut it down when the system halts/reboots.
So far, I have used the information here : [http://ubuntuforums.org/showthread.php?t=1704166](http://ubuntuforums.org/showthread.php?t=1704166)
To write the following script:```
#!/bin/bash

## Fill in name of program here.
PROG="otosense"
PROG_PATH="/usr/bin" ## Not need, but sometimes helpful (if $PROG resides in /opt for example).
PROG_ARGS="10000000" 
PID_PATH="/var/run/"


start() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, exit with error.
        echo "Error! $PROG is currently running!" 1>&2
        exit 1
    else
        ## TODO: Rename output file to something else, so a new one can be created...
    ## Change from /dev/null to something like /var/log/$PROG if you want to save output.
            $PROG_PATH/$PROG $PROG_ARGS 2>&1 >/var/log/$PROG/ &
        echo "$PROG started"
        touch "$PID_PATH/$PROG.pid"
    fi
}


stop() {
    if [ -e "$PID_PATH/$PROG.pid" ]; then
        ## Program is running, so stop it
        killall $PROG


        rm "$PID_PATH/$PROG.pid"
        
        echo "$PROG stopped"
    else
        ## Program is not running, exit with error.
        echo "Error! $PROG not started!" 1>&2
        exit 1
    fi
}




case "$1" in
    start)
        start
        exit 0
    ;;
    stop)
        stop
        exit 0
    ;;
    reload|restart|force-reload)
        stop
        start
        exit 0
    ;;
    **)
        echo "Usage: $0 {start|stop|reload}" 1>&2
        exit 1
    ;;
esac
```
But it doesn't work so far. I'm trying to start the program otosense, which is a bash script. the script runs in an infinite loop for as long as the system is running, so it would be inappropriate (I think) to run it directly as a boot script. 
The script doesn't run until late after boot, and when it does it tells me that otosense (my program I want to start) is already running. I can avoid this, I've found, if I preemptively go to /var/run/otosense.pid and delete it. Even with a pid file there, there was no process running: ps -A | grep otosense yields nothing. Is there an obvious mistake in my script?
I added it to init.d, for information, by copying my file to /etc/init.d and then running sudo update-rc.d startotosense defaults, which yielded correct output and a note about LSB information or something, which I thought I implemented correctly? No?
I'm a little out of my league here... :-D

---

