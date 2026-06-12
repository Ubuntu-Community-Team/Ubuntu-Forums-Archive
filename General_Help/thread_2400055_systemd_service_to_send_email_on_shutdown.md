---
title: "systemd service to send email on shutdown"
date: 2018-09-01
forum: General Help
---

### Post by jsylvia007 on 2018-09-01
Howdy all!

I've recently upgraded a server from 16.04 to 18.04, and my emailOnShutdown/Startup script stopped sending the shutdown notification.

The other servers work just fine, but their postfix instances point to this server's instance.  This server is the only one that reaches out to my ISP...  Any idea what could be wrong here?

```

[Unit]
Description=Run Scripts at Start and Stop
Wants=postfix.service
Requires=postfix.service network.service
After=postfix.service network.service bind9.service


[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/root/scripts/emailNotify.sh start
ExecStop=/root/scripts/emailNotify.sh stop

[Install]
WantedBy=multi-user.target

```

The emailNotify.sh script:

```

#!/bin/sh
### BEGIN INIT INFO
# Provides:          emailNotify
# Required-Start:    $local_fs $network
# Required-Stop:     $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: emailNotify
# Description:       Service to notify of system power functions.
### END INIT INFO
EMAIL="root@mydomain.com"
RESTARTSUBJECT="["`hostname`"] - System Startup"
SHUTDOWNSUBJECT="["`hostname`"] - System Shutdown"
RESTARTBODY="This is an automated message to notify you that "`hostname`" started successfully.
Start up Date and Time: "`date`
SHUTDOWNBODY="This is an automated message to notify you that "`hostname`" is shutting down.
Shutdown Date and Time: "`date`
LOCKFILE=/var/lock/emailNotify
RETVAL=0

  # Source function library.
  #  . /etc/init.d/functions
  . /lib/lsb/init-functions

 stop()
 {
  echo -n $"Sending Shutdown Email: "
  echo "${SHUTDOWNBODY}" | mutt -s "${SHUTDOWNSUBJECT}" ${EMAIL}
  RETVAL=$?
  sleep 5
  postqueue -f
  sleep 5
 if [ ${RETVAL} -eq 0 ]; then
  rm -f ${LOCKFILE}
  log_success_msg "Email Successfully Sent..."
  else
  log_failure_msg "Email Failure!!!"
  fi
  echo
  return ${RETVAL}
 }
start()
 {
 echo -n $"Sending Startup Email: "
 echo "${RESTARTBODY}" | mutt -s "${RESTARTSUBJECT}" ${EMAIL}
 RETVAL=$?
 postqueue -f
  if [ ${RETVAL} -eq 0 ]; then
  touch ${LOCKFILE}
  log_success_msg "Email Successfully Sent..."
  else
  log_failure_msg "Email Failure!!!"
   fi
   echo
  return ${RETVAL}
 }
case $1 in
 stop)
 stop
 ;;
 start)
 start
  ;;
 *)
esac
exit ${RETVAL}


```

I added the ```
postqueue -f
``` to the script so at least the queue gets flushed on reboot.  I think I'm missing a dependency, but I can't imagine what it is.

Any help?

---

