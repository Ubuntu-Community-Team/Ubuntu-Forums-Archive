---
title: "init.d script not loading"
date: 2016-09-13
forum: General Help
---

### Post by jesrani on 2016-09-13
I recently installed Ubuntu Mate 14.04 on a PC which was earlier running 12.04 successfully. Had to reinstall only because Hard disk died.
I have a particular script in /etc/init.d folder, made as per instructions in [https://ubuntuforums.org/showthread.php?t=637258](https://ubuntuforums.org/showthread.php?t=637258)
There are basically 3 files, /etc/automount.conf, /etc/init.d/automount and /usr/bin/local/automount
This mounts Windows shares and automatically creates the folders under a folder "/network". I am mainly using the PC headless to backup windows shares, from XP to Win7 to Win10 PC's
The script was running very well in 12.04.
It was also running after I installed 14.04. However now, after I updated the software, it doesn't run on start. When I run the command, "sudo /etc/init.d/automount" it runs, but not automatically.
What is wrong?
I have checked on the net for answers but could not get a solution. I have tried the command "sudo init-checkconf -d /etc/automount.conf" and get 
ERROR: File /etc/automount.conf: syntax invalid:
init:automount.conf:20: Unknown stanza
at the end.
How do I resolve this?

---

### Post by ian-weisser on 2016-09-13
Check your path. There shouldn't be a file at '[COLOR=#000000]/etc/automount.conf[/COLOR]'. Shouldn't it be '[COLOR=#000000]/etc/init.d/automount.conf[/COLOR]' ?

If that's just a typo entering it into the forum, then you have a syntax error at line 20 of that file. Fix it.
If you cannot locate it, show us the entire contents of the file.

---

### Post by jesrani on 2016-09-14
> **ian-weisser said:**
> Check your path. There shouldn't be a file at '[COLOR=#000000]/etc/automount.conf[/COLOR]'. Shouldn't it be '[COLOR=#000000]/etc/init.d/automount.conf[/COLOR]' ?

If that's just a typo entering it into the forum, then you have a syntax error at line 20 of that file. Fix it.
If you cannot locate it, show us the entire contents of the file.

The automunt.conf file has always been in /etc and not /etc/init since I have been using for past 8 years or more.
The contets of the /etc/automount.conf file is:

[B]# all lines that begin with comments (#) or are entirely blank are ignored
# the order of the options, share, and mount do not matter; autocreate cannot be first
# avoid excess white space at beginning or end of the options, share, and mount lines

# lines beginning with autocreate turn on autocreation (and auto removal) of the last mount directory
#   Note that autocreation may sometimes fail to remove the mount directory if unmounting
#   is not complete when it tries to delete it.  This will not cause any side effects.
# lines beginning with - are options lines
# lines beginning with // are share lines
# lines beginning with delay= set the delay between pings on the shares (in seconds)
#   This line can appear anywhere, and multiple times, but only the last value is saved
#   If the line is absent, the script defaults to a value of 60
# all other lines are assumed to be the mount location line

# Due to limitations in matching existing mounts, the no mount location should be a match
#   for a substring of a second mount
#   e.g., don't mount /media/blah and /media/blah2 or /blah
#   e.g., /media/blah, /media/2blah, and /mount/blah are all fine concurrently

delay=60

# IMPORTANT : FOR rsync to work, it is necessary to give full access to the shares
# Windows XP Computers, use cifs command
# Windows 98 computers, use smbfs command
# 24/5/08, had to add the servern=NETBIOSNAME for Ubuntu 8.04. Also need to use uppercase share name

# Backup2 (Win10 PC)
-t cifs -o rw,username=***,password=***,uid=1000,iocharset=utf8
//backup2/folder
/network/backup2
autocreate

# Admin (Win7 PC)
-t cifs -o username=***,password=***,user,rw,uid=1000
//admin/folder
/network/admin
autocreate[/B]

The contents of /etc/init.d/automount file are :

[B]#! /bin/sh
### BEGIN INIT INFO
# Provides:          N/A
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Automounts SAMBA shares
# Description:       Dynamically (un)mounts specific SAMBA shares.
### END INIT INFO

# Set info for messages
DESC="Automount shares"
NAME=automount
SCRIPTNAME=/etc/init.d/$NAME
DAEMON=/usr/local/bin/$NAME
PIDFILE=/var/run/$NAME.pid

# Exit if the daemon script is not installed
[ -x "$DAEMON" ] || exit 0

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

do_start()
{
  echo "Starting automount..."
  start-stop-daemon --start --quiet --background --make-pidfile --pidfile $PIDFILE --exec $DAEMON --test > /dev/null || return 1
  start-stop-daemon --start --quiet --background --make-pidfile --pidfile $PIDFILE --exec $DAEMON -- start $ConfFile || return 2
}

do_stop()
{
  echo "Stopping automount and unmounting..."
  start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
  RETVAL="$?"
  [ "$RETVAL" = 2 ] && return 2
  # Execute again w/ stop to unmount all
  $DAEMON stop $ConfFile
  rm -f $PIDFILE
  return "$RETVAL"
}

do_pause()
{
  echo "Stopping automount..."
  start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
  RETVAL="$?"
  [ "$RETVAL" = 2 ] && return 2
  rm -f $PIDFILE
  return "$RETVAL"
}

if [ "$2" = "" ] # no config file passed
then
  ConfFile=/etc/automount.conf # default configuration file
else
  ConfFile=$2
fi

case "$1" in
  start)
    [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
    do_stop
    do_start
    case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    exit "$?"
    ;;
  stop)
    [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
    do_stop
    case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    exit "$?"
    ;;
  force-reload|restart)
    [ "$VERBOSE" != no ] && log_daemon_msg "Restarting $DESC" "$NAME"
    do_stop
    case "$?" in
      0|1)
        do_start
        case "$?" in
          0) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
          1) [ "$VERBOSE" != no ] && log_end_msg 1 ;; # Old process is still running
          *) [ "$VERBOSE" != no ] && log_end_msg 1 ;; # Failed to start
        esac
        exit "$?"
        ;;
      *)
        # Failed to stop
        [ "$VERBOSE" != no ] && log_end_msg 1
        exit "$?"
        ;;
    esac
    ;;
  pause)
    [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
    do_pause
    case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
    esac
    exit "$?"
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload|pause} [FILE]"
    echo "  /etc/automount.conf will be used if FILE is not specified."
    exit 3
    ;;
esac

exit[/B]

Hope I get get a resolution to this issue.

---

### Post by jesrani on 2016-09-14
Ok... All seems to be working now. Seems there was some syntax problem due to which the network shares not getting mounted properly and taking long time to show up.

---

