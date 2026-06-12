---
title: "Shell Bash script help needed!"
date: 2008-07-06
forum: General Help
---

### Post by SvEnX on 2008-07-06
Hi,

Im tring to find a solution to run one shell script as a different user, so far i havent find anything from google or any where else and im too newb to figure it out my self. Iv tried to use su -c at the start of the script, but nothing....
can anyone help?

Script looks like this:


```

#!/bin/bash

APP_NAME="dedicated server"
EXE_NAME=name_of_executable
EXE_FILE=$EXE_NAME
APP_PATH=/home/username/server/
PID_FILE=/var/tmp/$EXE_NAME.pid
SCRIPT_NAME=name_of_server

if [ -r /lib/lsb/init-functions ]; then
	. /lib/lsb/init-functions
	LOG_BEGIN="log_begin_msg"
	LOG_END="log_end_msg"
else
	LOG_BEGIN="echo -n"
	LOG_END=`printf "echo .\n"`
fi

# Exit if the daemon binary is NOT available, executable, etc.
test -x $APP_PATH/$EXE_NAME || exit 0

start() {
	$LOG_BEGIN "Starting $APP_NAME: $EXE_NAME"
	LD_LIBRARY_PATH=$APP_PATH start-stop-daemon --start --pidfile $PID_FILE --make-pidfile $PID_FILE \
		--chdir $APP_PATH --background --exec $APP_PATH/$EXE_FILE \
		+parameters
	$LOG_END $?
}

stop() {
	$LOG_BEGIN "Stopping $APP_NAME: $EXE_NAME"
	start-stop-daemon --stop --pidfile $PID_FILE --chdir $APP_PATH
	$LOG_END $?
}

status() {
	if [ -e $PID_FILE ]; then
		echo "The $APP_NAME is running with a PID of `cat $PID_FILE`"
	else
		echo "The $APP_NAME is not running"
	fi
}

case "$1" in
	start)
		start
		;;
	stop)
		stop
		;;
	restart)
		stop
		sleep 1
		start
		;;
	status)
		status
		;;
	*)
        	log_success_msg "Usage: $SCRIPT_NAME {start|stop|reload|status}"
        	exit 1
        	;;
esac
exit 0


```

---

### Post by HalPomeranz on 2008-07-06
In general you run a script as another user with:

```

sudo -u username /path/to/your/script

```

If you want to run the script as root, then just:

```

sudo /path/to/your/script

```

---

### Post by SvEnX on 2008-07-06
> **HalPomeranz said:**
> In general you run a script as another user with:

```

sudo -u username /path/to/your/script

```

If you want to run the script as root, then just:

```

sudo /path/to/your/script

```

Thx it solved the problem...
added this to the script in bold

```
start() {
	$LOG_BEGIN "Starting $APP_NAME: $EXE_NAME"
	**sudo -u username** LD_LIBRARY_PATH=$APP_PATH start-stop-daemon --start --pidfile $PID_FILE --make-pidfile $PID_FILE \
		--chdir $APP_PATH --background --exec $APP_PATH/$EXE_FILE \
		+parameters
	$LOG_END $?
}

```

---

