---
title: "Getting Kubuntu to boot to KDM (graphical login) instead of console"
date: 2008-03-31
forum: General Help
---

### Post by FreeRangeChicken on 2008-03-31
I've recently installed Kubuntu Gutsy on a machine via the "Alternate" install CD.  The installation boots to a console login.  After logging into the console I can "startx" to get the window system running or I can run "kdm" to get the graphical login screen, so I know all of the KDE/KDM stuff is working.

I cannot figure out how to get the machine to boot to the KDM login instead of the console login.  I've crunched through a bunch of config files comparing them to those on another machine that boots to the KDM login.  The machine boots to runlevel 2, as does my other kubuntu machine which works.  I've added debug code to the /etc/rc2.d/S13kdm file and it *is* executing that file, but apparently deciding not to start kdm(presumably based on a config file setting somewhere.

 * I've tried "sudo dpkg-reconfigure kdm"
 * The  kdm service is set to run at startup
 * I've dug through config files
 * After running startx manually and scoured the "K-menu -> System Settings"

**Surely this is just a configuration flag somewhere, but I can't figure out where to turn it on.**

In the following code you can see the debug code I added to /etc/rc2.d/S13kdm to echo "checkpoints" to a log file.  It prints up to checkpoint 5, checkpoint 5b and later do not print to the log"... anyway, I know this file is executed when entering runlevel 2.


```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          x-display-manager kdm
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      console-screen
# Should-Stop:       console-screen
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: X display manager for KDE
# Description:       KDM manages a collection of X servers, which may be on the local host or remote machines.
### END INIT INFO
# /etc/init.d/kdm: start or stop the X display manager
# Script originally stolen from the xdm package
#
# description: K Display Manager
#
set -e

echo ">>>>>> Checkpoint 1 <<<<<<" >> /tmp/kdmstart.log

# To start kdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager

PATH=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/bin/kdm
PIDFILE=/var/run/kdm.pid
UPGRADEFILE=/var/run/kdm.upgrade

# parameters to support kdm customization
KDMRC=/etc/kde3/kdm/kdmrc
BACKGROUNDRC=/etc/kde3/kdm/backgroundrc

#if configuration is changed by kdmtheme or other tools, don't do magick
if grep -q "Theme=@@@ToBeReplacedByDesktopBase@@@" ${KDMRC} && grep -q "Wallpaper=default_blue.jpg" ${BACKGROUNDRC}
then



KDMOVERRIDEDIR=/etc/default/kdm.d
KDMCFGDIR=/var/run/kdm
KDMCFG=$KDMCFGDIR/kdmrc
BACKGROUNDCFG=$KDMCFGDIR/backgroundrc

echo ">>>>>> Checkpoint 2 <<<<<<" >> /tmp/kdmstart.log

test -x $DAEMON || exit 0

echo ">>>>>> Checkpoint 3 <<<<<<" >> /tmp/kdmstart.log

# uncomment, if you want auto-logon to be runlevel-dependant
#test "$runlevel" || { runlevel=`runlevel`; runlevel=${runlevel#* }; }
#test "$runlevel" = 4 && ARG=-autolog || ARG=-noautolog

# uncomment, if you want tons of debug info in your syslog
#ARG="$ARG -debug 255"

# we use an alternative kdm master configuration file
ARG="$ARG -config $KDMCFG"

# we source overrides. run-parts sorts the list in a predictable order
if [ -d "$KDMOVERRIDEDIR" ]; then
    for part in $(run-parts --list "$KDMOVERRIDEDIR" 2>/dev/null || true); do
        . "$part"
    done
fi

echo ">>>>>> Checkpoint 4 <<<<<<" >> /tmp/kdmstart.log

# we generate kdm configuration files
genkdmconf --in $KDMCFGDIR 1> /dev/null

# we update kdm configuration files (only overridden values)
[ -n "$USEBACKGROUND" ] && sed -i "s|^#\?UseBackground=.*|UseBackground=$USEBACKGROUND|" $KDMCFG
[ -n "$BACKGROUNDCFG" ] && sed -i "s|^#\?BackgroundCfg=.*|BackgroundCfg=$BACKGROUNDCFG|" $KDMCFG
[ -n "$USETHEME" ] && sed -i "s|^#\?UseTheme=.*|UseTheme=$USETHEME|" $KDMCFG
[ -n "$THEME" ] && sed -i "s|^#\?Theme=.*|Theme=$THEME|" $KDMCFG
[ -n "$WALLPAPER" ] && sed -i "s|^#\?Wallpaper=.*|Wallpaper=`readlink -f $WALLPAPER`|" $BACKGROUNDCFG

echo ">>>>>> Checkpoint 5 <<<<<<" >> /tmp/kdmstart.log

# we get the system default locale if USESYSTEMLOCALE is set to true
$USESYSTEMLOCALE && sed -i "s|^#\?Language=.*|Language=`grep -re "LANG=" /etc/default/locale | awk 'BEGIN { FS = "[\\"|.]" } { print $2 }'`|" $KDMCFG

echo ">>>>>> Checkpoint 5b <<<<<<" >> /tmp/kdmstart.log

fi

# autologin overrides are useful for live debian environment
if [ -n "$AUTOLOGINUSER" ]; then
	sed -i "s|^#\?AutoLoginEnable=.*|AutoLoginEnable=true|" $KDMCFG
	sed -i "s|^#\?AutoLoginUser=.*|AutoLoginUser=$AUTOLOGINUSER|" $KDMCFG
fi

echo ">>>>>> Checkpoint 7 <<<<<<" >> /tmp/kdmstart.log

[ -n "$AUTOLOGINDELAY" ] && sed -i "s|^#\?AutoLoginDelay=.*|AutoLoginDelay=$AUTOLOGINDELAY|" $KDMCFG
[ -n "$AUTOLOGINAGAIN" ] && sed -i "s|^#\?AutoLoginAgain=.*|AutoLoginAgain=$AUTOLOGINAGAIN|" $KDMCFG
[ -n "$AUTOLOGINLOCKED" ] && sed -i "s|^#\?AutoLoginLocked=.*|AutoLoginLocked=$AUTOLOGINLOCKED|" $KDMCFG

echo ">>>>>> Checkpoint 8 <<<<<<" >> /tmp/kdmstart.log

# If we upgraded the daemon, we can't use the --exec argument to
# start-stop-daemon since the inode will have changed.  The risk here is that
# in a situation where the daemon died, its pidfile was not cleaned up, and
# some other process is now running under that pid, start-stop-daemon will send
# signals to an innocent process.  However, this seems like a corner case.
# C'est la vie!
if [ -e $UPGRADEFILE ]; then
  SSD_ARGS="--pidfile $PIDFILE --startas $DAEMON"
else
  SSD_ARGS="--pidfile $PIDFILE --exec $DAEMON"
fi

echo ">>>>>> Checkpoint 9 <<<<<<" >> /tmp/kdmstart.log

stillrunning () {
  if expr "$(cat /proc/$DAEMONPID/cmdline 2> /dev/null)" : "$DAEMON" > /dev/null 2>&1; then
    true
  else
    # if the daemon does not remove its own pidfile, we will
    rm -f $PIDFILE $UPGRADEFILE
    false
  fi;
}

case "$1" in
  start)
    if [ -e $DEFAULT_DISPLAY_MANAGER_FILE ] &&
       [ "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" ] &&
       [ "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
      echo "Not starting K Display Manager (kdm); it is not the default display manager."
    else
      # if usplash is runing, make sure to stop it now, yes "start" kills it.
      if pidof usplash > /dev/null; then
         DO_NOT_SWITCH_VT=yes /etc/init.d/usplash start
      fi

      echo -n "Starting K Display Manager: kdm"
      start-stop-daemon --start --quiet $SSD_ARGS -- $ARG || echo -n " already running"
      echo "."
    fi
  ;;

  restart)
    /etc/init.d/kdm stop
    if [ -f $PIDFILE ]; then
      if stillrunning; then
        exit 1
      fi
    fi
    /etc/init.d/kdm start
  ;;

  reload)
    echo -n "Reloading K Display Manager configuration..."
    if start-stop-daemon --stop --signal 1 --quiet $SSD_ARGS; then
      echo "done."
    else
      echo "kdm not running."
    fi
  ;;

  force-reload)
    /etc/init.d/kdm reload
  ;;

  stop)
    echo -n "Stopping K Display Manager: kdm"
    if [ ! -f $PIDFILE ]; then
      echo " not running ($PIDFILE not found)."
      exit 0
    else
      DAEMONPID=$(cat $PIDFILE | tr -d '[:blank:]')
      KILLCOUNT=1
      if [ ! -e $UPGRADEFILE ]; then
        if start-stop-daemon --stop --quiet $SSD_ARGS; then
          # give kdm's signal handler a second to catch its breath
          sleep 1
        else
          echo -n " not running"
        fi
      fi
      while [ $KILLCOUNT -le 5 ]; do
        if stillrunning; then
          kill $DAEMONPID
        else
          break
        fi
        sleep 1
        KILLCOUNT=$(( $KILLCOUNT + 1 ))
      done
      if stillrunning; then
        echo -n " not responding to TERM signal (pid $DAEMONPID)"
      else
        rm -f $UPGRADEFILE
      fi
    fi
    echo "."

    # Launches usplash on shutdown
    if ( `grep -q '\( \|^\)splash\( \|$\)' /proc/cmdline` && `which usplash_down >/dev/null` ) ; then
      usplash_down
    fi
  ;;

  *)
    echo "Usage: /etc/init.d/kdm {start|stop|restart|reload|force-reload}"
    exit 1
    ;;
esac

echo ">>>>>> Checkpoint End <<<<<<" >> /tmp/kdmstart.log
exit 0
```


Further info:
This is an install on a Playstation 3.  I used the Gutsy Alternate install CD because it was the only one available for PS3.  The fact that kdm and startx commands work suggest that it is just a configuration issue.  I believe the "Alternate" CDs default to a console login.



Thanks in advance, 

Dave

---

### Post by bwhite82 on 2008-03-31
Try simply reconfiguring the package first:
> sudo dpkg-reconfigure kdm

---

### Post by FreeRangeChicken on 2008-03-31
> **Soldierboy said:**
> Try simply reconfiguring the package first:

Thanks for the reply, Soldierboy.

I've tried "sudo dpkg-reconfigure kdm" and also "sudo apt-get --reinstall install kdm" neither of which have changed the behavior.

Grrr, frustrating.  I'm sure this is a very simple flag somewhere.

---

### Post by bwhite82 on 2008-03-31
What are the results of:
> cat /etc/X11/default-display-manager

It should be:
> /usr/sbin/kdm

If not there, then add it to the file and try it.

EDIT: Also found this page: [http://www.linuxforums.org/forum/debian-linux-help/24831-boot-into-gui-2.html](http://www.linuxforums.org/forum/debian-linux-help/24831-boot-into-gui-2.html)

---

### Post by FreeRangeChicken on 2008-03-31
> **Soldierboy said:**
> What are the results of...

Yep, "/etc/X11/default-display-manager" contains "/usr/sbin/kdm"

---

### Post by bwhite82 on 2008-03-31
Alright, we'll get there eventually :)
Install a useful app:
> sudo apt-get install sysv-rc-conf

Run it:
> sudo sysv-rc-conf

See where the "x" is for kdm.

You should have an "x" on runlevels 2,3,4 and 5.

---

### Post by FreeRangeChicken on 2008-03-31
X's are at 2, 3, 4, 5 

This is alluded to in /etc/rc2.d/S13kdm (this file is a symbolic link to /etc/init.d/kdm)


/etc/init.d/kdm excerpt...
```

### BEGIN INIT INFO
# Provides:          x-display-manager kdm
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      console-screen
# Should-Stop:       console-screen
**_# Default-Start:     2 3 4 5_**
# Default-Stop:      0 1 6
# Short-Description: X display manager for KDE
# Description:       KDM manages a collection of X servers, which may be on the local host or remote machines.
### END INIT INFO

```

---

### Post by bwhite82 on 2008-03-31
Wow, have been googling for the last half hour and gotta say...i'm stumped.

---

### Post by bwhite82 on 2008-03-31
Did you happen to install Splashy?

---

### Post by FreeRangeChicken on 2008-03-31
Yeah, I've done a ton of googling, too, to no avail.

I have not installed splashy.

---

### Post by bwhite82 on 2008-03-31
Another "hack" I just read about, add the following line to /etc/rc.local just before the "exit 0" line:
> kdm &

---

### Post by FreeRangeChicken on 2008-03-31
More info...

New discovery.  I tried to start the kdm service and got a response that is probably a clue.

> 
freerangechicken@ps3:~$ sudo /etc/init.d/kdm start
sed: -e expression #1, char 32: unterminated `s' command


Looking at the section between "Checkpoint 5" and Checkpoint 5b" in the "/etc/init.d/kdm" file above, there is a sed command between CP-5 and CP-5b.  CP-5 logs to the file, CP-5b does not.  Looks like this line is the culprit.


RESOLVED!!!

That was it.  The line between CP-5 and CP-5b was grabbing the locale from "/etc/default/locale"  Turns out this fille contained an extra line that was choking things up.

/etc/default/locale
```
LANG="en_US.UTF-8"
LANG="en_US.UTF-8"
```


**Deleting the extra line fixed the problem.**

That was a head-scratcher.

Thanks for your time, Soldierboy.

Dave

---

### Post by bwhite82 on 2008-03-31
Wow, that was quite obscure, glad you got it all sorted out though. Perhaps you should file a bug report?

---

### Post by FreeRangeChicken on 2008-04-01
> **Soldierboy said:**
> Wow, that was quite obscure, glad you got it all sorted out though. Perhaps you should file a bug report?

Done.  I submitted a bug report at [https://bugs.launchpad.net/ubuntu/+bug/210287]("https://bugs.launchpad.net/ubuntu/+bug/210287")

---

### Post by Yaba on 2008-04-03
Do you really have /usr/**_s_**bin/kdm in your /etc/X11/default-display-manager? If yes, change that to /usr/bin/kdm (bin, instead of sbin). The startup script /etc/init.d/kdm checks, if the content of default-display-manager is exactly that string. Also a space at the end of this line or a newline char may break this.

---

### Post by FreeRangeChicken on 2008-04-03
> **Yaba said:**
> Do you really have /usr/**_s_**bin/kdm in your /etc/X11/default-display-manager? If yes, change that to /usr/bin/kdm (bin, instead of sbin). The startup script /etc/init.d/kdm checks, if the content of default-display-manager is exactly that string. Also a space at the end of this line or a newline char may break this.


Actually, it is "/usr/bin/kdm" (not sbin).  Sorry for the misinformation.  Good eye.


Fixing the double entry in the "\etc\default\locale" file resolved the issue.

---

