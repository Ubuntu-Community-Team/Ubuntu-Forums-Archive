---
title: "How to Troubleshoot Services that don't start"
date: 2007-08-15
forum: General Help
---

### Post by jfrankman on 2007-08-15
I have been trying to get the JBoss application server to automatically startup. I have done the same sort of thing on SUSE without problems, but I can't get this working on Ubuntu 7. I don't need a JBoss expert here I just need to know where to look to find why my service is not starting. Is there a log somewhere I can look at? My current configuration is as follows:

OS: Ubuntu 7
I have created a start up script named 'jboss' in /etc/init.d/jboss. 
I have created a symbolid link named S21jboss in the /etc/rc5.d directory. (i originally had the link in rc3.d and rc4.d but have just put it in rc5.d until I can get this working.)

I can run the script manually without problems: /etc/rc5.d/S21jboss start
The script is configured to log everything to a jboss.log file. But when a restart the computer nothing gets logged to this file. It is as if Ubuntu did not even try to execute the S21jboss at all.

The contents of my jboss startup script are:

#! /bin/sh
#
# $Id: jboss_init_redhat.sh 46554 2006-07-28 10:29:13Z dimitris $
#
# JBoss Control Script
#
# To use this script run it as root - it will switch to the specified user
#
# Here is a little (and extremely primitive) startup/shutdown script
# for RedHat systems. It assumes that JBoss lives in /usr/local/jboss,
# it's run by user 'jboss' and JDK binaries are in /usr/local/jdk/bin.
# All this can be changed in the script itself. 
#
# Either modify this script for your requirements or just ensure that
# the following variables are set correctly before calling the script.

#define where jboss is - this is the directory containing directories log, bin, conf etc
JBOSS_HOME=${JBOSS_HOME:-"/usr/local/jboss-4.0.5.ejb3"}
echo "james was here"
#define the user under which jboss will run, or use 'RUNASIS' to run as the current user
#JBOSS_USER=${JBOSS_USER:-"jboss"}
JBOSS_USER=${JBOSS_USER:-"RUNASIS"}

#make sure java is in your path
JAVAPTH=${JAVAPTH:-"/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin"}

#configuration to use, usually one of 'minimal', 'default', 'all'
JBOSS_CONF=${JBOSS_CONF:-"default"}

#bind address for jboss services, by default bind to *all* NICs
JBOSS_HOST=${JBOSS_HOST:-"0.0.0.0"}

#define the classpath for the shutdown class
JBOSSCP=${JBOSSCP:-"$JBOSS_HOME/bin/shutdown.jar:$JBOSS_HOME/client/jnet.jar"}

#define the script to use to start jboss
JBOSSSH=${JBOSSSH:-"sudo $JBOSS_HOME/bin/run.sh -c $JBOSS_CONF -b $JBOSS_HOST"}

if [ "$JBOSS_USER" = "RUNASIS" ]; then
  SUBIT=""
else
  SUBIT="su - $JBOSS_USER -c "
fi

if [ -n "$JBOSS_CONSOLE" -a ! -d "$JBOSS_CONSOLE" ]; then
  # ensure the file exists
  touch $JBOSS_CONSOLE
  if [ ! -z "$SUBIT" ]; then
    chown $JBOSS_USER $JBOSS_CONSOLE
  fi 
fi

if [ -n "$JBOSS_CONSOLE" -a ! -f "$JBOSS_CONSOLE" ]; then
  echo "WARNING: location for saving console log invalid: $JBOSS_CONSOLE"
  echo "WARNING: ignoring it and using /dev/null"
  JBOSS_CONSOLE="/dev/null"
fi

#define what will be done with the console log
#JBOSS_CONSOLE=${JBOSS_CONSOLE:-"/dev/null"}
JBOSS_CONSOLE=${JBOSS_CONSOLE:-"$JBOSS_HOME/log/jboss.log"}

JBOSS_CMD_START="cd $JBOSS_HOME/bin; $JBOSSSH"
JBOSS_CMD_STOP=${JBOSS_CMD_STOP:-"java -classpath $JBOSSCP org.jboss.Shutdown --shutdown"}

if [ -z "`echo $PATH | grep $JAVAPTH`" ]; then
  export PATH=$PATH:$JAVAPTH
fi

if [ ! -d "$JBOSS_HOME" ]; then
  echo JBOSS_HOME does not exist as a valid directory : $JBOSS_HOME
  exit 1
fi

echo JBOSS_CMD_START = $JBOSS_CMD_START

case "$1" in
start)
    cd $JBOSS_HOME/bin
    if [ -z "$SUBIT" ]; then
        eval $JBOSS_CMD_START >${JBOSS_CONSOLE} 2>&1 &
    else
        $SUBIT "$JBOSS_CMD_START >${JBOSS_CONSOLE} 2>&1 &" 
    fi
    ;;
stop)
    if [ -z "$SUBIT" ]; then
        $JBOSS_CMD_STOP
    else
        $SUBIT "$JBOSS_CMD_STOP"
    fi 
    ;;
restart)
    $0 stop
    $0 start
    ;;
*)
    echo "usage: $0 (start|stop|restart|help)"
esac

exit 0

If this question belongs in the newbie forums let me know. Anyone's help on where to find logging information about the startup process would be appreciated.

Thanks.

---

### Post by Jussi Kukkonen on 2007-08-15
The answer may be easier than you think: Ubuntu default runlevel is 2, so you should put your symlink in /etc/rc2.d/

---

### Post by jfrankman on 2007-08-15
I am running Ubuntu with a GUI (GNOME) so even if I did not have a symlink in rc2.d wouldn't my script have started when Ubuntu hit runlevel 5?

---

### Post by Jussi Kukkonen on 2007-09-13
Sorry. I missed your reply. I guess you've already found out the answer... 

Just to make sure: Debian and Ubuntu runlevel for X (and Gnome) is not 5 it is 2 like I tried to explain.

---

